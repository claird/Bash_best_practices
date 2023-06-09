# echo-vs-printf

It's time for one of your **Bash**-coded applications to write a bit of content to the console, or perhaps a filesystem.  How do you do so?

## Dramatic personae

Most of us learn `echo` early in our **Bash** careers.  `echo` is so capable that it's possible to code successfully for _years_ without touching
on `printf` as an alternative to `echo`.  What's
the point of the latter, then?  Is one just like the other, with a default terminal `newline`?  Do experienced coders have any reason more interesting
than [pretension](https://softwareengineering.stackexchange.com/questions/64416/do-programmers-sometimes-intentionally-over-complicate-code) for their frequent use of `printf`?

There _is_, in fact, more to the story.  While quite a few commentators apparently believe that "[... [t]he only difference ... is `echo` will
output an extra newline
...](https://unix.stackexchange.com/questions/58310/difference-between-printf-and-echo-in-bash#:~:text=Both%20echo%20and%20printf%20are%20built-in%20commands%20%28printf,gives%20a%20non-zero%20exit%20status%20code%20upon%20failure.)",
that's not the whole truth:
* `printf` is better standardized;
* The two differ especially in how they handle **escape characters**; and
* `echo`'s variations are large enough to constitute **security surprises**.

## Standardization

On MacOS 13.2.1, for instance, `/bin/bash` pops up as `... version 3.2.57 ...`  Modern Linux distributions tend to operate with version 5.1.4 or greater.  The `echo` available within `/bin/bash` behaves differently with regard to `-n` in versions 3.2 and before, compared to 4.0 and later.  One summary:  "[Applications aiming for maximum portability are strongly encouraged to use `printf` ...](https://nixdoc.net/man-pages/freebsd/man8/man1/echo.1.html)"
Also, "[... `printf` is a preferred alternative ...](https://www.man7.org/linux/man-pages/man1/echo.1.html)"

Conclusion:  the behavior of [`printf` is more uniform](https://www.in-ulm.de/~mascheck/various/echo+printf/)
across different `bash` environments than is that of `echo`.  Bluntly,
"[... there's never a good reason to use `echo` ...](https://askubuntu.com/questions/467747/which-is-better-printf-or-echo#:~:text=The%20only%20reason%20to%20use%20echo%20rather%20than,there%27s%20never%20a%20good%20reason%20to%20use%20echo.)"

## Escape characters

More recent `echo` doesn't honor escaped characters.  More specifically, `S='ab\tcd\n'; echo "$S"; printf "$S"; printf %s "$S"` with most
current Linuxes results in
```bash
ab\tcd\n
ab	cd
ab\tcd\n
```

while on MacOS one sees
```bash
ab	cd

ab	cd
ab\tcd\n
```

## Security

Although `echo` can be easier, and perhaps require fewer keystrokes, to program in common cases, the examples above make it clear that
[`printf` is more consistent and flexible across different environments](https://www.in-ulm.de/~mascheck/various/echo+printf/).
`echo`'s surprises are so many that its use arguably creates [security hazards](https://mywiki.wooledge.org/BashPitfalls#echo_.24foo).

[Provide explicit example of security risk.]

## Performance considerations

[Production-level](https://stackoverflow.com/questions/3908038/what-is-production-level-code) **Bash** programming probably is best off to eschew `echo` entirely, in favor of `printf`.  To repeat the conclusions above:
`printf` is more consistent and manageable.

However, [`echo` _is_ faster](https://unix.stackexchange.com/questions/65803/why-is-printf-better-than-echo/159115#159115).  On yet another hand,
if you have a [production-level program](https://dev.to/doma/everything-you-need-to-know-to-write-safe-bash-scripts-17gg) [follow up with
essay on safe **Bash** programming?] where `echo`'s speed advantage is consequential ... well,
[you probably need a more delicate analysis](https://unix.stackexchange.com/questions/297792/how-complex-can-a-program-be-written-in-pure-bash)
than fits in this little essay.  As a starting point:  don't leave home without [**ShellCheck**](https://www.shellcheck.net/) [provide page on **ShellCheck**].

## printf vs print

[Explain.  Explain `print -r ...`]

# Why do these notes appear here rather than in Stackoverflow or elsewhere?

[Explain.  No advertising.  Just documented, pertinent facts.]
