# echo-vs-printf

It's time for one of your **Bash**-coded applications to write a bit of content to the console, or perhaps a filesystem.  How do you do so?

## Dramatic personae

Most of us learn `echo` early in our **Bash** careers.  `echo` is so capable that it's possible to code successfully for _years_ without touching
on `printf`.  What's
the point of the latter, then?  Is one just like the other, with a default terminal `newline`?  Do experienced coders have any reason stronger
than pretense for their frequent use of `printf`?

There _is_, in fact, more to the story.  While quite a few commentators apparently believe that "[... [t]he only difference ... is `echo` will
output an extra newline
...](https://unix.stackexchange.com/questions/58310/difference-between-printf-and-echo-in-bash#:~:text=Both%20echo%20and%20printf%20are%20built-in%20commands%20%28printf,gives%20a%20non-zero%20exit%20status%20code%20upon%20failure.)",
that's not the whole truth:
* `printf` is better standardized;
* The two differ in how they hande **escape characters**; ...
* [... security ...]

## Standardization

On MacOS 13.2.1, for instance, `/bin/bash` pops up as `... version 3.2.57 ...`  Modern Linux distributions tend to operate with version 5.1.4 or greater.

...
