---
Title: On Kakoune
Date: 2026-08-03
Draft: True
---

*Are you tired of lacking real skills and need a
superficial victory over VS Code users with more accomplishments
than you? Would you like to eschew your neutrality and enlist in
an age-old war?*

*Then which will it be? E--- or V---?*

![Kakoune editing Itself](editing-kakoune.png "Kakoune editing
Itself")

{{< break >}}

For a little over a month, I've been using
[Kakoune](https://kakoune.org), a modal code editor
much like V---, for all my writing. I've used it to spit
out a couple poems, a few thousand words of [interactive
fiction](https://github.com/ericsmoore/papillon), plenty of notes,
a post plus and several drafts for this site, and a bit of code.

I have not written this to tell you why Kakoune is the best
editor, even though it is. That has already been done by others
better than I ever could. Nor am I going to teach you how to
use it, for the same reason. I do, however, aim to introduce a
unique perspective on how I'm using Kakoune for both creative
writing and code.

## A Prose Editor

Writing prose in plain-text is certainly not a novel idea. Look no
further than the popularity of Markdown, Org Mode, Obsidian, and
the rest. For simplicity and portability, it is unbeatable. Plain
text is going nowhere.

The [First Kakoune Community Survey][survey], conducted in 2020,
found, unsurprisingly, that only eight out of 142 respondents
using Kakoune for work were using it primarily for writing prose.
I would love to hear if any of the few Kakoune users out there
are enjoying the editor for writing on the more creative side,
like I am.

If there are many others, they must not be sharing their
experience or, what we truly care about, their configuration.
This is what V--- and E--- users have on us. Being the definitive
end-game editors for decades has done a lot for those who insist
on using them for prose.

Fortunately, Kakoune has everything I
need.

### Object Mode

Kakoune recognizes sentence and paragraph objects in the
various object modes. For example, consider moving around a
paragraph. `<a-a>p` selects around the current paragraph including
the following blank line, `<a-i>p` selects only the paragraph
text, `]p` selects to the end of the surrounding paragraph and
`}p` extends the selection as well. We also have consistent
results with `{p` and `[p`, which work on the beginning of
the paragraph. If that isn't enough, we can select inside the
paragraph block by prefixing any of those 4 commands with alt
(equivalent to the difference between using `<a-i>p` instead of
`<a-a>p`).

<!--### Wrapping

There is heated debate on the proper way to wrap plain text when
writing in markdown and similar formats. I am yet undecided.
Unfortunately, and perhaps my only significant complaint with
Kakoune, is that it does not properly support soft-wrapping text.
I am saving this issue for another time where it might have room
to breathe.

Fortunately, Kakoune does a decent job of automatically
hard-wrapping text using external tools. It works well 95% of the
time.-->

## A Code Editor


## Further Reading

- [Why Kakoune, Maxime Coste][why]
- [Design Notes][design]

[survey]: https://kakoune-editor.github.io/community-articles/2020/12/12/results_interpretation_first_community_survey.html
[design]: https://github.com/mawww/kakoune/blob/master/doc/design.asciidoc
[why]: https://kakoune.org/why-kakoune/why-kakoune.html

