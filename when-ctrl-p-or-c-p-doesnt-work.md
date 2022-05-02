# When Ctrl-P (or C-p) Doesn't Work

tl;dr Add "detachKeys" : "C-\\,C-q" to ~/.docker/config.json

## Problem

When you hit Ctrl-p, the bash prompt (or IRB or python prompt) does not scroll up. If you hit it again, it goes up 2 lines.

Or, If You're Starting To Catch On: When you hit Ctrl-p, the prompt _does_ seem to go back--it just doesn't redraw.

## Explanation

It's not you, it's Docker. It captures C-p C-q to allow detaching, which could be SUPER useful if you weren't already running it from inside tmux. You may use that C-p C-e works

## Solution

tl;dr Add "detachKeys" : "C-\\,C-q" to ~/.docker/config.json. If the file doesn't already exist, make it a root-level key in a simple hash, like:

```
{
  "detachKeys" : "C-\\,C-q"
}
```

This will change the detach hotkey sequence to C-\ C-q.

## Workarounds

Guest on another machine? Try starting/running the container docker with `--detachKeys="C-\\,C-p"`.

## Coping

Can't use either workaround? Get used to `C-p C-e` (`<ctldown> p e <ctlup>`). &shrug;
