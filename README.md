`fontpreview-ueberzug` is a bash(1) script to preview all fonts installed on system in `fzf` with `ueberzug`. It is inspired by [fontpreview](https://github.com/sdushantha/fontpreview) project while most of the code are completely rewritten here.

(1): It has only a minimal dependency on non-POSIX feature of `printf` command, which is printing Unicode characters with more than 16-bit code point. Most of the script is still POSIX-complaint. (If anyone knows how to do that within POSIX, don't hesitate to tell)

![](./demo.gif)

## Dependencies

- [`fzf`](https://github.com/junegunn/fzf)
- [`ueberzug`](https://github.com/seebye/ueberzug)
- `imagemagick`

## Install

### Manual

Simply run the script, or put the script in your `$PATH`, or with provided makefile.

### AUR

For Arch based users, `fontpreview-ueberzug-git` is available [in AUR](https://aur.archlinux.org/packages/fontpreview-ueberzug-git), thanks to @pabloariasal!

## Usage

```
Usage: fontpreview-ueberzug [-h] [-a TEXT_ALIGN] [-s FONT_SIZE] [-b BG_COLOR] [-f FG_COLOR] [-t PREVIEW_TEXT]

Options:
    -a     alignment of preview text, you can use center, top/bottom/left/right or
           north/south/west/east, or combinations like topleft, default is center
    -s     preview font size, default is 72, note the actual size depends on the preview area
    -b, -f background and foreground color, default is #ffffff and #000000
    -t     preview text, you can add '\n' to split into lines
```

The arguments are passed directly to 'convert' command, you can check the ImageMagick documentation to find acceptable formats for them.

### Tips

- To merge the preview image into the terminal, set background color the same as that of the terminal emulator, this is not by default.

- To show ligatures, you can use the following or any other text which contains ligature combination:
```
FONTPREVIEW_PREVIEW_TEXT="ABCDEFGHIJKLM\nNOPQRSTUVWXYZ\nabcdefghijklm\nnopqrstuvwxyz\n1234567890\n<!-- != == ->\n-| #[ |> <$> ~@" fontpreview-ueberzug
```

## Configure

This script makes use of some of the environment variables as follows, these are the same in [fontpreview](https://github.com/sdushantha/fontpreview) so you can use the same settings with `fontpreview-ueberzug`:

- `FONTPREVIEW_FONT_SIZE`
- `FONTPREVIEW_BG_COLOR`
- `FONTPREVIEW_FG_COLOR`
- `FONTPREVIEW_PREVIEW_TEXT`
- `FONTPREVIEW_TEXT_ALIGN`

## Difference from [fontpreview](https://github.com/sdushantha/fontpreview)

- Does not need two windows (terminal and sxiv) to display. Use `ueberzug` to display the preview image in terminal instead.
- Preview updates as you scroll without having to press enter also going back to the first font in list.
