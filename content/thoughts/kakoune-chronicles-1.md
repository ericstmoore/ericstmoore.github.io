---
Title: "Kakoune Chronicles I"
Subtitle: Windowing
Date: 2026-07-31
code: true
---

I currently have two separate kakoune utilities that differ only
by three words. I define commands for splits and new tabs under
the same name, one for sway and one for tmux. The only difference
is the single word at the beggining of the terminal command.

```kak
define-command split -params .. -command-completion \
    -docstring "split [<commands>]: split sway horizontally" %{
    sway-terminal-vertical kak -c %val{session} -e "%arg{@}"
}
```

All I need to do is comment out one or the other source line in my
kakrc, and since they use the same command names, my keybinds
don't need to change.

This is obviously a bad solution, and I know it.

For one, kakoune already autodetects the windowing environment.
The `new` command will work in tmux, sway, even apple terminal.
I should be able to use the idea to define the proper command
automatically.

Inspecing the `new` command, I see that it uses `terminal` to
determine the preferred terminal emulator.

`terminal` creates a new temminal window based on the
preferred(detected?) windowing environment. A program with
optional arguments must be passed, for example `sh`, to run in the
window.

Actually, `terminal` is more of a helper command to call the
specific commands provided by kakoune's windowing detection. When
you execute `terminal`, you are actually just executing:

```kak
"%opt{windowing_module}-terminal-%opt{windowing-placement}"
```

The solution is as easy as using `windowing_module` in my own
command. You do need the quotes around the command. If I knew more
about kakoune's script parsing I might could explain it. I can't.

```kak
define-command split -params .. -command-completion \
    -docstring "split [<commands>]: split tmux horizontally" %{
    "%opt{windowing_module}-terminal-vertical" \
    kak -c %val{session} -e "%arg{@}"
}
```

There might be more you can do here, but this works for me.
