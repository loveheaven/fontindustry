| English | [中文](FontIndustryZhCN.md) |
|:--------|:--------------------------|

万事开头难，所以就先开了这么个头

# Font Industry 字体工业 #

Copyright (c) Hashao 2007
License: GNU GPL version 3 or later. Please see the included LICENSE file.

字体制造的工业化革命

Font Industry industrialize procedure of the big charset font production. It
free the big charset font creation from artists' studio into the average John's
basement. The font market will be flooded with huge amount of <sub>cheap</sub>, ~~low
quality~~, **big charset**, _hand script_ fonts in no time. Be scared! Be very scared!

What does Font Industry really do?

The program converts a scanned in grid sheet containing a lot of glyphs into a bitmap font. The glyphs will be automatically indexed with unicode. That's it.

The bitmap font format used is the fontforge .sfd.

An **outline font** (TTF, OpenType/OTF) can then be generated using fontforge's
autotrace function.

A separated **grid sheet template package** is provided.

## Dependency ##

  * Python >=2.4
  * Pygtk
  * Pygoocanvas: GooCanvas python binding. python-pygoocanvas in Debian.
  * Python-gconf. (On Debian box, it's included in the python-gnome2 package now)
  * Python Imaging Library (called python-imaging in Debian).        http://www.pythonware.com/products/pil/

  * You will also want to install [FontForge](http://fontforge.sourceforge.net/) and [potrace](http://potrace.sf.net/)/[autotrace](http://autotrace.sourceforge.net/) for scalable font creation. They will be automatically recognized once installed. See http://fontforge.sourceforge.net/autotrace.html for more information.

Of course you should also have:
  * Pens
  * Paper
  * Scanner (For bulk scanning job, a scanner with _Auto Document Feeder_ is recommended. Some Multi-Function Printers will come with one.)

## Screenshots ##

[Some screenshots here](ScreenShot.md).

## Download ##
http://code.google.com/p/fontindustry/downloads/list

## Usage ##
[Link to the usage page](Usage.md).

Note:

> The command name is **fontin**.

> 程序名称为: **fontin**

## Mailing List ##
|User: | http://groups.google.com/group/fontindustry-user/topics |
|:-----|:--------------------------------------------------------|
|Developer: | http://groups.google.com/group/fontindustry-dev/topics  |

## Tools ##
> ### Grid Paper ###
> > A simple tool to generate grid sheet template in .svg format. Get it in the [download page](http://code.google.com/p/fontindustry/downloads/list).

## Links ##
  * [hashao's other projects](http://hashao.googlecode.com/)

## News ##
2008-10-12:
  * Version 0.0.9
  * Update family name to the sfd font.
  * Add the zoom image function.
  * When set glyph from text, try selected text first.
  * Move "Set End" button to the toolbar.
  * Misc bug fixes.

2008-10-01:
  * Release CenterGlyph　0.1.
  * A FontForge plugin to auto central aligns selected glyphs.

2008-07-18:
  * Version 0.0.8
  * Handle invalid encoding for unicode
  * Convert to utf-8 before saving pathname for non-latin1 pathname.
  * Fix mouse abnormal for large image
  * Handle both RGB (jpeg) and RGBA images
  * Generate font using UnicodeFull encoding
  * Add function to set glyph unicode from a piece of string
  * Add menuitem to clear charcode for all the glyphs
  * Create a new application icon
  * Add rpm, deb package files (might be buggy, please report)
  * Fix some setup.py problem

2008-03-05:
  * Release 0.0.7
  * Major bug fix: Save current glyph order while saving new font.
  * Add GB2312 as a glyph order option.

2008-03-02:
  * Release 0.0.6
  * Sort the current glyphs by font charset in the font view dialog.

2008-02-29:
  * Add 96, 48 cell grid papers to the template package. The GB2312 charset has a structure of 94 glyphs per region. GBK has a structure of 2\*96=192 glyphs per region. 48\*2=96 cells.
  * Upload gridpaper-0.1.tar.bz2, the tool which was used to generate the grid template.

2008-02-26:
  * Add some grid templates in PDF format. User can print the templates out and use the templates as guide while writing glyphs.

2008-01-19:
  * Version 0.0.5.
  * When export to .sfd font, set some sane tags for the font.
  * Change ascend/descent to 880/120 and add LineGap to 200.
  * Add 4 standard glyphs to the begining of a font.
  * Add a image list pan for mass importing glyph sheet.
  * Minor bug fixes.

2008-01-10:
  * Version 0.0.4
  * Fix some bugs here and there.
  * Character point can be changed in Font View Dialog.

2007-12-31:
  * Version 0.0.3
  * Fix a bug which keep font from being saved to disk. shelve cache thing.
  * Add a dialog to view and edit current font content.
  * More document on code.

2007-12-27:
  * Version 0.0.2
  * Fix a bug which prevent font from being saved in some situation (When the first glyph is not set to a character).
  * Add 'compact' header field to the .sfd file.

2007-12-23:
  * Release early, release often cut. Very little test. Please test it.