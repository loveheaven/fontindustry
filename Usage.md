| English | [中文](UsageZhCN.md) |
|:--------|:-------------------|

[<- Back to the main page](FontIndustry.md)

Here are the procedures on how to write your own font. Yes, write the font, not create one.

Basic procedures:
> open image->create grid->generate character index->save font->export .sfd.
## Screencast ##
  1. [Font Industry Screencast 01](http://fontindustry.googlecode.com/svn/wiki/screenshots/fontindustry-screencast01.avi) (8.6MB): Tutorial to create a TTF font from a low quality screen capture image.
> > The quality of the final TTF is kinda poor because the resolution of the original image is quite low. 1 square inch (~3cm) glyphs scanned in at 300dpi or 600dpi should yield better result.
  1. [Font Industry Screencast 02](http://fontindustry.googlecode.com/svn/wiki/screenshots/fontindustry-screencast02.avi) (15MB): Tutorial on the "Set Charcodes to String" function.
> > Sample pages of a book from an online library was used. The book can be found at http://nla.gov.au/nla.gen-vn1889757. The images were pre-processed manually with Gimp.


## Steps ##
Note: The executable name is **fontin**.
  1. Print out a page of grid template. It will be used as a guide while writing glyphs. (Download grid templates from [here](http://fontindustry.googlecode.com/files/gridTemplates-1.1.tar.bz2))
> > Hint: For charset GB2312/GBK, a 96 cell glyph sheet make it easier to track code point. A 48 cell glyph sheet can be used for big calligraphy.
  1. Write your font glyphs on a piece of paper. Use the grid template created above as the background. Write the glyphs in the code order for the charset of your choice.
> > Tip: Use a clip to stick the foreground and background papers together.
  1. Scan in the sheet at 300dpi/600dpi or higher resolution. Save images in the .png format.
  1. Start the Font Industry (the command is 'fontin').
  1. Open the scanned image with Font Industry (File->**Open Image**)
  1. Drag the rubber bands to set the glyph cell size.
> > Tips: Adjust the right and the bottom bands first such that they are at the middle of characters; then adjust the left and the top bands to make the margins symmetric.
  1. Create the grid lines for the image. (Action->**Create Grid**)
  1. Repeat 6 to 7 until you are satisfied with the grid.
  1. Unset the click buttons in the cell to mark bad cells.
  1. Select a charset order from the Order combo box.
  1. Set a start character for the set of glyph (Action->**Generate Characters**)
> > You can type in a single character or type in a hex code of the character e.g. 0xa1a1.
  1. Save the result into Font Industry's native font file. (File->**Save**)
  1. Load another glyph sheet and repeat above steps until all your glyph sheet are processed.
  1. Generate fontforge's .sfd font. (File->**Export to FontForge**)
  1. Open the resulting .sfd font in fontforge.
  1. Export the font into a bitmap font (File->**Generate Font**).
  1. Open a new font, import the previous bitmap font as background. (File->Import... and select As Background)
  1. Select all the glyphs. (Edit->Select->Select All)
  1. Ask **fontforge** to autotrace your font to scalable font. (Element->**Autotrace**)
> > More information about autotrace can be found at [fontforge's autotrace page](http://fontforge.sourceforge.net/autotrace.html).
  1. Fine touch the font, set proper font informations.
  1. Select all and Remove the background images. (Edit->Clear Background)
  1. Export to OpenType, TrueType font. (File->**Generate Font**)
  1. ...
  1. Profit!


**P.S.** You can hint an _end cell_ by focus on the cell and click the "Toggle End" button. Any cells after this cell will be treated as garbage.

Well, I am sorry that it takes your more than 20 steps to get to the profit part, but it is actually quite fast once you get to know the streamline.

## Image Pre-processing ##
You are suggested to pre-process the scanned images with [mkbitmap](http://potrace.sourceforge.net/mkbitmap.html) before use the images in the font industry. mkbitmap is a utility of the [potrace](http://potrace.sourceforge.net) program. For example:
```
convert image.png ppm:- |mkbitmap -n -s 3 -t 0.52 |convert pbm:- -type Palette -quality 0 blackwhite-image.png
```
which converts an image by turn off the high pass filter(-n), then scale up by 3 (-s 3) and finally, convert to black & white bitmap using 52% of black as the middle point (-t 0.52). `convert` is a tool of [ImageMagick](http://www.imagemagick.org/index.php). `convert` can be used to do much more work on image pre-processing.

Since the high pass filter was turned off completely, we can achieve the same result using `convert` only:
```
convert -resize 300% -threshold 52% -type Palette -quality 0 image.png blackwhite.png
```

In a batch nut shell:
```
#!/bin/sh
for i in "$@" ; do
 outname="bw-${i}.png"
 echo "Saving to ${outname}..."
 convert "$i" ppm:- | mkbitmap -n -s 3  -t 0.52  | convert pbm:- -type Palette -quality 0 "${outname}"
 #convert "$i" -resize 300% -threshold 52% -type Palette -quality 0 "${outname}"
done
```

Enjoy your own hand writing font and FLOOD the font market. Don't let me down.

## Charset Table ##
When write your own font, you will need a grid sheet and a character set table of your character set.
  * [GBK Version 1](http://fontindustry.googlecode.com/svn/wiki/charcharts/GBK1.txt). Or step to the [evil side](http://www.microsoft.com/globaldev/reference/dbcs/936.mspx).
  * [GB2312 for Simplified Hanzi only](http://fontindustry.googlecode.com/svn/wiki/charcharts/GB2312.txt). Hanzi start from 0xB0A1.

  * [Unicode Hanzi 统一码汉字](http://www.unicode.org/versions/Unicode5.0.0/cjkcharts.html)
  * [Unicode char table for all languages](http://www.unicode.org/charts/)