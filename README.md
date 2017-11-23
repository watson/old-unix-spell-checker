# Old UNIX Spell Checker

In an old video from Bell Labs, [Brian
Kernighan](https://en.wikipedia.org/wiki/Brian_Kernighan) introduces the
audience to the concept of pipelines in UNIX systems using a simple
spell checking example:

[![AT&T Archives: The UNIX Operating
System](https://img.youtube.com/vi/tc4ROCJYbm0/0.jpg)](https://youtu.be/tc4ROCJYbm0?t=384)

Most of the programs used in the spell checking example are not present
in modern UNIX variants. For fun I wanted to see how easy it would be to
recreate the same capabilities today.

The example operates on a text file called
[`sentence`](https://github.com/watson/old-unix-spell-checker/blob/master/sentence):

```
At Bell Laborotories
UNIX systems privide
more timesharing ports
than all other systems
combined
```

The original chain of commands used in the video are:

```
makewords sentence | lowercase | sort | unique | mismatch
```

Only the `sort` program still exists today. And the `unique` program
have been renamed to `uniq` on most systems.

This means we need to re-create `makewords`, `lowercase` and `mismatch`.
This repository contains those 3 programs.

To run them locally, simply clone this reporsitory and run the following
pipeline:

```
./makewords sentence | ./lowercase | sort | uniq | ./mismatch
```

The output of this command is:

```
laborotories
ports
privide
systems
timesharing
unix
```

For more awesome old videos of computer history, check out [Awesome
Conputer History](https://github.com/watson/awesome-computer-history).

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, [Thomas
Watson](https://github.com/watson) has waived all copyright and related
or neighboring rights to this work.
