# Personal fork of st (Simple terminal implementation for X)
[st's official webpage](st.suckless.org) Original source code at: [git.suckless.org/dwm/](git.suckless.org/st/).

[Original st's README.](STREADME)

## Patches applied
If not declared otherwise, assume most recent version for all mentioned patches.
- [Alpha](https://st.suckless.org/patches/alpha/): This patch allows users to change the opacity of the background. Note that you need an X composite manager (e.g. compton, xcompmgr) to make this patch effective. 
- [Scrollback](https://st.suckless.org/patches/scrollback/): Scroll back through terminal output using Shift+{PageUp, PageDown}. Note: The patches "scrollback-mouse", "scrollback-mouse-altscreen" and "scrollback-mouse-increment" were not applied.
- [Blinking cursor](https://st.suckless.org/patches/blinking_cursor/): This patch allows the use of a blinking cursor.
- [Xresources](https://st.suckless.org/patches/xresources/): This patch adds the ability to configure st via Xresources. At startup, st will read and apply the resources named in the resources[] array in config.h.
- [Newterm](https://st.suckless.org/patches/newterm/): This patch allows you to spawn a new st terminal using Ctrl-Shift-Return. It will have the same CWD (current working directory) as the original st instance.
- [Font2](https://st.suckless.org/patches/font2/): This patch allows to add spare font besides default. Some glyphs can be not present in default font. For this glyphs st uses font-config and try to find them in font cache first. This patch append fonts defined in font2 variable to the beginning of font cache. So they will be used first for glyphs that absent in default font.

## Emoji support
Unlike with [dwm](https://github.com/brlipi/dwm/) and [dmenu](https://github.com/brlipi/dmenu/), st does not have any code to prevent it from crashing when it has to print an emoji. This is not the fault of the program but rather the library used by it. The font2 patch does not break anything nor does it fix the issue. The [xft-bgra fix for libXft](https://gitlab.freedesktop.org/xorg/lib/libxft/-/merge_requests/1/diffs?commit_id=b77e5752cbd4acef90904e00c0f392984c321ca9) is needed for st to be able to render emojis and not crash.

## Installation
After cloning this repository in the directory of your choice, then if you wish to change its default namespace installation (/usr/local), edit the `config.mk` file. Afterwards run `sudo make clean install`
