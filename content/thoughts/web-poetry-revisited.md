---
Title: Web Poetry Revisited
Date: 2026-08-09
---

After reading Gwern's [article](https://gwern.net/poetry-html)
on typesetting poetry in {{< sc >}}html{{< /sc >}}, I wanted
to revisit the [post](/thoughts/poetry-infrastructure) I wrote
on the same topic in March. My method of choice, which Gwern
calls "semantic class soup", was dismissed in the article as
"a *compilation target* for some poetry {{< sc >}} dsl{{<
/sc >}}."[^1]

I don't entirely agree with the criticism that authoring poetry
by "encoding all the semantics" into classes is difficult---were
we ever writing poetry directly in {{< sc >}}html{{< /sc >}}
anyway?[^2] A simple script can convert text into the proper {{<
sc >}}html{{< /sc >}} immediately. I can understand if you're
working in an environment where fonts, containers, styles, and
all other kinds of presentation might be more complicated. If
you need to make manual edits, I can agree that you probably
don't want class soup.

The better argument centers on the poem's lack of accessibility in
nonstandard reading environments. Screen-readers will certainly
struggle with the unusual semantics, and if {{< sc >}}css{{<
/sc >}} falls out, you lose the indentation that was stuffed
away in the padding. Even with everything loading perfectly,
copy-pasting will flatten the spacing since it was never there
to begin with.

In the end it seems that proper accessibility and semantic design
are fundamentally incompatible with good typesetting on the
web. With poetry particularly, if dynamic enjambment/indentation
is a priority, a simple solution without JavaScript is elusive.
Of course, if you're not like me and don't hate JavaScript,
you can wrap the text however you please, even breaking at the
least disruptive points.[^3]


Looking for some answers online, I noticed that both the
[Poetry Foundation](https://www.poetryfoundation.org) and
the [Academy of American Poets](https://poets.org) keep
things simple: Unicode spaces at the start of lines and the
`padding-left: 1; text-indent: -1;` trick for simple hanging
indentation. It doesn't work with multiple levels of
indentation, and so I improved upon it for my own [poetry
infrastructure](/thoughts/poetry-infrastructure).

However, I don't feel proud of my battle with the Poetry
Foundation anymore. Yes, my solution looks better on tiny
screens when the text wraps, but, at that size, it was going
to look bad anyway. And, to get there, I gave up the ability
to copy the poem with indentation, and I tied all of it to a
few fragile lines of {{< sc >}}css{{< /sc >}}.

I'm going to keep it around for now. If needed, I can always link
to the original plain text poem. I plan to continue looking for
some way to have indentation with real spaces, and yet keep the
dynamic hanging indent. I do believe it is possible somehow.[^4]



[^1]: <https://gwern.net/poetry-html#semantic-class-soup>

[^2]: This is actually a very interesting question to me,
especially since I've been thinking a lot about hypertext
literature in the last month. Most poems reaching the web were
probably not written with the web in mind, I assume, and so to
frame this as an issue of authoring feels like a distraction.
Writing a poem to live on the web is a different thing altogether,
and, to me, the medium somehow demands interacting with the soup.
It is not, unless you make it one, a fixed 5 by 8 inch page on
which you write a poem, and it is part of the process to decide
how to handle that.

[^3]: See <https://gwern.net/poetry-html#nicer-line-breaking>.
I accept that this level of design is beyond the capabilities
of pure {{< sc >}}html{{< /sc >}} and {{< sc >}}css{{< /sc >}},
but I don't see the value anyway. If you care that much about
the formatting of your poem, you should just distribute a {{<
sc >}}pdf{{< /sc >}}

[^4]: My best idea so far: If we can guarantee the right font
loads (now also restricted to that single font), we can match
the width of a space to the unit used in our {{< sc >}}css{{<
/sc >}}. This unfortunately introduces a new problem: if the
font fails to load but the {{< sc >}}css{{< /sc >}} loads fine,
our indentation would be out of alignment. Changing fonts would
also be a nightmare if you have to recalibrate the spacing.
