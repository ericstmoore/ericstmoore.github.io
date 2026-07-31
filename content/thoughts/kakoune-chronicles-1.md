---
Title: "Kakoune Chronicles I"
Subtitle: Windowing
Date: 2026-07-31
code: true
---

I had two separate, nearly identical
[Kakoune](https://kakoune.org) scripts to open a new terminal in
either Sway or tmux and connect to the
session.[*](https://discuss.kakoune.com/t/split-kakoune-windows-with-tmux/325/5)
In other words, for making splits and tabs, panes and windows, or
whatever else you might call them.

```kak
define-command vsplit -params .. -command-completion \
    -docstring "vsplit [<commands>]: new vertical split" %{
    sway-terminal-vertical kak -c %val{session} -e "%arg{@}"
}
```

All I had to do was comment out the line that sources the one not
being used in my `kakrc`. Both use the same names for the commands
so my keybinds don't need to change.

```kak
# using tmux
source "%val{config}/utils/tmux.kak"
# source "%val{config}/utils/sway.kak"
```

This is obviously a horrible solution. You could load them
conditionally at the cost of a subshell, but this is unnecessary.

For one, Kakoune's system scripts already do this to auto-detect
the windowing environment. The `new` command will work in tmux,
sway, even the macOS Terminal.app. You can use the same idea to
define the proper command automatically.

Inspecting `new`, you'll see that it uses the `terminal` command
to determine the preferred terminal emulator. `terminal` creates
a new terminal window based on the detected windowing
environment. A program with optional arguments must be passed,
for example `sh`, to run in the window.

Actually, `terminal` is more of a helper command to call the
specific commands provided by Kakoune's windowing detection. When
you execute `terminal`, you are actually just executing:

```kak
"%opt{windowing_module}-terminal-%opt{windowing-placement}"
```

The solution to combining the two windowing utilities is as easy
as using the `windowing_module` option in the command as done in
`terminal`.

```kak
define-command hsplit -params .. -command-completion \
    -docstring "hsplit [<commands>]: new horizontal split" %{
    "%opt{windowing_module}-terminal-horizontal" \
    kak -c %val{session} -e "%arg{@}"
}
```

{{< break >}}

It is worth noting that Kakoune does not auto-detect
multiple/nested windowing environments. For example, if you use
tmux in Sway, you do not have access to the `sway-terminal-`
commands, but only those from tmux. However, you can manually
load them with `require-module sway`. This opens up possibilities
for some pretty complicated and unnecessary windowing plugins.
