# Today I Learned
A random collection of things I've learned and forgotten and relearned and
reforgotten and so on...

## Bash
* `2>&1` - Pipe STDERR to STDOUT so it can be captured with >.
* `man re_format 7` - The full man page documentation for POSIX Regular
  Expressions

## Disk Usage Quick and Easy
* `du -hs ./*` - Don't use man du and then use -d 1 to trim depth, that ONLY
  gives you disk usage one layer deep. -s will SUM up the disk space used, and
  passing ./* means sum up the space for EACH folder involved. The -h is just
  there to provide human-friendly output (e.g. 700M or 4.1G)

## Emacs
* `M-x package-refresh-contents` - This is `apt-get update` for MELPA. Use this
  when `package-install` tells you a package is present but running it fails
  with an error about the packgage+timestamp.tgz could not be found.

## RubyGems
* Do I want colorize or term-ansicolor?
  * http://flori.github.io/term-ansicolor/
  * If you're only going to learn one, learn term-ansicolor and manually add the
    `class String; include Term::ANSIColor; end` monkeypatch to make it behave
    like colorize.
  * If you want more power, term-ansicolor has FAR more colorizing power. Run
    `term_colortab`, `term_mandel`, or `term_display <imagefile>` in bash for
    cool demos.
  * If you already know colorize and it does everything you want and you don't
    want the hassle, just stick with that. Colorize can add strings cleanly
    and I haven't figure out how to do that in term-ansicolor yet.

But `term-ansicolor` is FAR more powerful. It has a bajillion colors and
includes a bunch of cool demos like `term_mandel` or `term_display <imagefile>`
(brew/apt install netpbm to support image formats other than pbm). If you're
only going to learn one, learn term-ansicolor and get used to this shorthand:

TL;DR: If someone who loves `colorize` asks why you use `term_ansicolor`, show
them the difference here:

```bash
$ ruby -rcolorize -e 'puts String.color_samples'
$ term_colortab
```

Or, if they're from CMM, show them this. It's subtle and you have to work hard
for it but if you value this sort of thing like I do you'll get it:


```bash
$ ruby -rcolorize -e 'puts "cover".bold.yellow.on_white +
"my".bold.magenta.on_white + "meds".bold.yellow.on_white'

$ ruby -rterm/ansicolor -e 'c=Object.new.extend Term::ANSIColor; print c.bold,
c.on_white, Term::ANSIColor::RGBTriple[ [247, 141, 37] ].color("cover"), c.bold,
c.on_white, Term::ANSIColor::RGBTriple[ [ 160, 0, 64 ] ].color("my"), c.bold,
c.on_white, Term::ANSIColor::RGBTriple[ [247, 141, 37] ].color("meds"), "\n"'
```

(See covermymeds-term-ansicolor.txt and covermymeds-colorize.txt in this repo
for example output)

## Random

## Other
Things that don't fit in any other category--not even Random
