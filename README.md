`fontpreview-ueberzug` is a POSIX shell script to preview all fonts installed on system in `fzf` with `ueberzug`. It is inspired by [fontpreview](https://github.com/sdushantha/fontpreview) project while most of the code are completely rewritten here.

![](./demo.gif)

## Dependencies

- [`fzf`](https://github.com/junegunn/fzf)
- [`ueberzug`](https://github.com/seebye/ueberzug)
- `imagemagick`

## Install

### Manual

Simply run the script, or put the script in your `$PATH`, or with makefile as follows:

After cloning/downloading the repo, install with make (change the destination with `PREFIX`)
```
make install
```

### AUR

For Arch based users, `fontpreview-ueberzug-git` is available [in AUR](https://aur.archlinux.org/packages/fontpreview-ueberzug-git), thanks to @pabloariasal!

## Usage

```
Usage: fontpreview-ueberzug [-h] [-s FONT_SIZE] [-b BG_COLOR] [-f FG_COLOR] [-t PREVIEW_TEXT] [-p WIDTHxHEIGHT]

Options:
   -h show help message
   -s font size
   -b background color
   -f foreground color
   -t preview text
	 -p preview size (e. g. 640x480)
```

### Tips

To merge the preview image into the terminal, set background color the same as that of the terminal emulator, this is not by default.

To show ligatures, you can use the following or any other text which contains ligature combination:
```
FONTPREVIEW_PREVIEW_TEXT="ABCDEFGHIJKLM\nNOPQRSTUVWXYZ\nabcdefghijklm\nnopqrstuvwxyz\n1234567890\n<!-- != == ->\n-| #[ |> <$> ~@" fontpreview-ueberzug
```

## Configure

This script makes use of some of the environment variables as follows, these are the same in [fontpreview](https://github.com/sdushantha/fontpreview) so you can use the same settings with `fontpreview-ueberzug`:

- `FONTPREVIEW_FONT_SIZE`: Font size
- `FONTPREVIEW_BG_COLOR`: Background color
- `FONTPREVIEW_FG_COLOR`: Foreground color
- `FONTPREVIEW_PREVIEW_TEXT`: Preview text to display
- `FONTPREVIEW_SIZE`: Preview size

## Difference from [fontpreview](https://github.com/sdushantha/fontpreview)

- Does not need two windows (terminal and sxiv) to display. Use `ueberzug` to display the preview image in terminal instead.
- Preview updates as you scroll without having to press enter also going back to the first font in list.
