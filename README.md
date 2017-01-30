# Kobo ePub Guidelines
What’s in this Document:
 
* Elements of the ePub spec that Kobo does and does not support.
* Features of the five Kobo reading platforms.
* Recommendations on file production and testing for content creators. 
 

### Table of Contents

1. [ePub Versions Kobo Supports](#epub-versions-kobo-supports)
2. [Kobo Reading Platforms](#kobo-serves-content-to-users-on-these-5-reading-platforms)
3. [Kobo Devices](#current-kobo-devices)
5. [Kobo Recommends Initial ePub Check](#kobo-recommends-initial-epub-check)
6. [Sideloading for Testing Purposes](#sideloading-for-testing-purposes)
7. [Digital Rights Management (DRM)](#digital-rights-management-drm)
8. [Image Formatting](#image-formatting)
9. [Cover Images](#cover-images)
10. [Scalable Vector Graphics (SVG)](#scalable-vector-graphics-svg)
11. [Table of Contents (ToC)](#table-of-contents-toc)
12. [OPF](#opf)
13. [CSS](#css)
14. [Supported Fonts](#supported-fonts)
15. [Obfuscated Fonts](#obfuscated-fonts-are-not-currently-supported-by-the-kobo-cms)
16. [Embedded Fonts](#embedded-fonts-can-be-selected-by-users)
17. [Embedding All Fonts in Fixed Layout] (#all-fonts-used-in-fixed-layout-content-must-be-embedded-and-cannot-be-modified)
18. [Languages](#languages-other-than-english)
19. [Right to Left Page and Text Direction] (#right-to-left-page-and-text-direction)
20. [Footnotes/Endnotes](#footnotesendnotes-are-fully-supported-across-kobo-platforms)
21. [Fixed Layout](#fixed-layout-fxl-support)
22. [SMIL](#kobo-supports-smil)
23. [Image-Based FXL Reader](#image-based-fxl-reader)
24. [Multimedia Support / Media Overlays](#multimedia-support--media-overlays)
25. [JavaScript Support](#javascript-support)
26. [MathML](#mathml-is-supported-on-ios-elnk-and-desktop-platforms)
27. [Fallback Statements](#fallback-statements)
28. [ePub Previews](#epub-previews)
29. [Tables](#tables)
30. [Limitations and Maximums](#limitations-and-maximums)
31. [Support Grid] (#support-grid)
32. [Common QA Failure Issues](#common-qa-failure-issues)
	* [Pixelated or Low Resolution Images](#pixelated-or-low-resolution-images)
	* [Missing Images](#missing-images)
	* [Blocks Appearing in Place of Text on Desktop and eInk Platforms](#blocks-appearing-in-place-of-text-on-desktop-and-eink-platforms)
	* [Font Obfuscation](#font-obfuscation)
	* [Text Spacing and Overlap Issues](#text-spacing-and-overlap-issues)
	* [Viewport Issues](#viewport-issues)
	* [Read-Along issues](#read-along-issues)
	* [Audio Video Issues on Android and iOS Platforms](#audio-video-issues-on-android-and-ios-platforms)
33. [Questions?](#still-have-questions)

### ePub Versions Kobo Supports
 
Kobo supports ePub, the universal open standard eBook format maintained by the Independent Digital Publishing Forum [(IDPF)](http://idpf.org/epub). The current version is ePub 3 but Kobo still supports its predecessor, ePub 2.0.1.

Any ePub file sent to Kobo will be made available on all of Kobo's reading platforms with the exception of ePub2 Fixed Layout content which is not available on Desktop or eInk:

| Platform                | ePub2 Reflowable | ePub2 FXL | ePub3 Reflowable | ePub3 FXL |
|-------------------------|------------------|-----------|------------------|-----------|
| Android                 | Y                | Y         | Y                | Y         |
| Desktop                 | Y                | N         | Y                | Y         |
| eInk                    | Y                | N         | Y                | Y         |
| iOS                     | Y                | Y         | Y                | Y         |
| Windows                 | Y                | Y         | Y                | Y         |
| Sony eReader            | Y                | N         | Y                | Y&#42;&#42;       |
| Kobo Vox&#42;               | Y                | Y         | Y                | N         |
| Blackberry&#42;             | Y                | N         | N                | N         |
| Original Kobo/Kobo WiFi | Y                | N         | N                | N         |

&#42;The Kobo Vox and Blackberry apps both run older versions/ports of the Android app and will not be updated.

&#42;&#42;Fixed Layout content display on Sony Readers is dependant on the capabilities of Adobe SDK. As a result the display of Fixed Layout content may not always match the display across other Kobo reading platforms.
 
The ePub 3.0 spec is based on HTML5 and CSS3, adhering to the most recent versions. Content creators are advised to review the [HTML5 and CSS3 reference profiles](http://www.idpf.org/epub/30/spec/epub30-contentdocs.html#references) because changes to them could impact file production. 
 
Kobo supports a subset of elements from the ePub 3.0 spec. The following covers which elements are supported across Kobo’s reading platforms.

**Kobo does not accept** .mobi, KF8, PDF or any format outside of ePub that may be used to format eBooks.

### Kobo Serves Content to Users On These 5 Reading Platforms 
 
1. eInk/EPD — Kobo eInk devices (Aura, Glo, Touch) 
2. Desktop — the Kobo desktop app for PC and Apple Computers
3. Android — all Android devices running the Kobo app including all Kobo Arc versions
4. iOS — iPad, iPhone and iPod Touch
5. Windows — all tablets, smartphones and computers running Windows apps.

### Current Kobo Devices

eInk:
* Touch 2.0
* Aura H2O
* Aura
* Aura One

### Earlier Kobo Devices
 
Android:
* Arc 7 SD
* Arc 7 HD
* Arc 10 HD
* Arc (original)
* Vox

eInk:
* Aura HD
* Glo HD
* Glo
* Kobo Mini
* Touch
* Kobo WiFi
* Kobo1
 
### Kobo Recommends Initial ePub Check 
 
The Kobo CMS does not use a built in ePubCheck. To detect errors in ePubs, the IDPF provides both a [web validation tool](http://validator.idpf.org/) and a [desktop application](https://github.com/IDPF/epubcheck). Kobo cannot guarantee that files that fail ePubCheck will render correctly across its reading platforms. So ePubs should be validated using the most recent version of ePubCheck prior to distribution. 
 
The Kobo Content Management System will neither reject those files that fail ePubCheck nor send reports to their publishers. However, if any rendering or performance issues harm the user experience, the files may be flagged for, and then failed in, the Kobo content QA process. 

Kobo recommends content creators remove any files not listed in the OPF document, as suggested by the validator. Leaving these files in the ePub can cause unexpected behaviour that may result in failing QA test results.

### Sideloading for Testing Purposes
 
Kobo encourages the testing of content on all its reading platforms by sideloading. Content should display identically whether sideloaded or downloaded to a device from the Kobo store. Instances where this is not the case can be reported to renderingissues@kobo.com and the epub in question will be logged for investigation. The only present exception applies to ePubs containing obfuscated fonts which will display correctly when sideloaded but will not pass content QA once processed - see [Font Obfuscation] (https://github.com/kobolabs/epub-spec/blob/master/README.md#obfuscated-fonts-are-not-currently-supported-by-the-kobo-cms).

Here’s how to sideload content on Kobo's reading platforms:
 
**eInk**

1. Connect the device to your computer via USB.
2. Find the drive on your computer in Finder or Windows Explorer.
3. Drag your ePub onto the device. To trigger the Kobo WebKit, change the file extension to “.kepub.epub”. To trigger the Kobo Webkit for a Fixed Layout title, change the extension to “.fxl.kepub.epub”. (If the extension is left unchanged it will render using the Adobe Digital Editions Webkit. This is the default display engine for side-loaded content to enable bookmarking, searching and highlighting.)
4. Disconnect your device. The file will automatically appear in your library.

*Sideloaded ePubs with the ".fxl.kepub.epub" or ".kepub.epub" will disable bookmarking and note keeping. Thumbnails for covers may not display. Otherwise the reading experience and content display will be identical to how the file would display when loaded through the store.
 
 
**Desktop**

1. Open the Kobo Desktop app.
2. Make sure you have [Adobe Digital Editions](http://www.adobe.com/ca/products/digital-editions/download.html) installed. If you do not wish to install ADE you can skip this step by creating a folder named "My Digital Editions" in your "My Documents" folder.
3. Select the Library tab in Kobo Desktop and press CTRL+Shift+S on Windows or ⌘+SHIFT+S on a Mac. This will display any files in the “My Digital Editions” folder on your computer with the extension .epub
 
**Android**

1. Connect the device to your computer via USB.
2. Find the drive on your computer in Windows Explorer. If you use a Mac, install and connect to the device using [Android File Transfer](http://www.android.com/filetransfer/).
3. Drag your ePub onto the device.
4. If you use a Kobo Arc, navigate to the Books Collection. Otherwise, navigate to the Kobo App, then tap the side bar menu icon on the top left (the icon with the three horizontal bars vertically stacked) to bring out the sidebar. Then tap on either 'All' or 'All Items' based on your app version.
5. Select options (the three dots on the top right) then “Import”.
6. Once the files appear, confirm that you want to import them. They will display in your library.
 
**iOS**

1. Connect the device to your computer with the iOS cable.
2. Open iTunes and navigate to iPad -> Apps.
3. Select the Kobo app from the box on the left.
4. Drag the ePub to the box in the bottom right of your iTunes window. If drag and drop functionality is not working then select the "Add file..." button and select the ePub you want to add to the app. The file will then automatically import and display in your library.

(The Kobo iOS app is registered among apps that open ePub and pdf files. Users can use the standard “open in…” menu from Safari, Dropbox, or any other app that supports it to view their files.)
 
**Windows**

1. Open the Kobo app, navigate to the Library and swipe up from the bottom of the screen.
2. Select “import”.
3. Select the files on the device that you want to import. (The Kobo app will scan all the files on your device that it can import. You may not be able to transfer files via USB depending on the specific Windows device and may need to transfer them by OneDrive, Dropbox, email or some other method instead.)
4. Select “Open” and wait for the files to load into your library.

### Digital Rights Management (DRM)
 
ePubs loaded to the Kobo store are protected by Kobo DRM. Kobo can turn the DRM off at the publisher-level, when publishers make a request to the Publisher Operations team.
 
Kobo’s DRM system hosts content on its reading platforms using advanced security methods, including the use of encryption and hash algorithms. Various keys are used to encrypt content before it is sent to the reading platform. There are unique keys for each eBook, user and device. 
 
At a minimum, Kobo employs encryption standards in the 128-bit version of the Advanced Encryption Standard (AES) of the US Government.
 
### Image Formatting
 
Kobo reading platforms support the core image types outlined in the [IDPF spec](http://www.idpf.org/epub/30/spec/epub30-publications.html#cmt-grp-image). This includes JPG, PNG and GIF but not Scalable Vector Graphics (SVG), which are not supported on all reading platforms. (See the Support Grid.) PNG files are preferred over JPG.
 
All images should use the RGB color model, and not CMYK. Encapsulated PostScript (EPS) images are not supported on Kobo.
 
**The advised maximum size for all image types is 5 MB.** ePubs with larger images are still accepted and those images will not cause Kobo apps and devices to crash. However, ePubs with images all under this limit perform optimally across platforms.

**Image dimensions should be set in percentages instead of pixels in the CSS for reflowable content.** Images with dimensions set by pixels may stretch depending on the orientation, device and user settings. Kobo reading platforms insert max-width and max-height CSS for images and videos to ensures that they are not split over multiple screens.

**Images should not have transparent backgrounds.** This will result in the reading system inserting a default background color or pattern. Fixed Layout titles with where image backgrounds are transparent will fail QA in cases where the content is unreadable.
 
**For a full screen image view** on the Android and iOS platforms, users can long press images in reflowable ePubs. Once in full-screen view, users will be able to pinch and zoom. This can also be acheived on eInk devices (running version 3.14 or later) by double tapping images.

**Scaling images may prevent them from displaying on eInk and Desktop.** Some ePubs will rotate and shrink images down to the size of a single pixel and then blow them back up to the intended view size. This will work on Android, iOS and Windows but on Desktop it results in the image either not displaying at all or only displaying as a single pixel.

Ex.</br>
`<g transform="matrix(850.4 0 0 680.3 0 0)">`</br>
    `<image width="1" height="1" transform="matrix(1 0 0 -1 0 1)" preserveAspectRatio="none" image-rendering="optimizeSpeed" xlink:href="images/GrandRendezVous_002.jpg"/>`</br>
`</g>`</br>

If the content is formatted this way instead it will display correctly on all Kobo platforms (note that the image will still be rotated but not shrunken):</br>
`<g>` </br>
    `<image width="850" height="680" transform="matrix(1 0 0 -1 0 680)" preserveAspectRatio="none" image-rendering="optimizeSpeed" xlink:href="images/GrandRendezVous_001.jpg"/>`</br>
`</g>`</br>

### Cover Images
 
If an external cover image is uploaded to both the Kobo system and the ePub, that external image displays as the thumbnail image in the store and in user’s libraries. The internal ePub cover still displays when the user opens the file on their device. External cover images must have the ISBN in the filename ex. "9781234567890.jpg" or "9781234567890.png".
 
GIF files are not supported for covers.
 
The suggested optimal ratio for covers on Kobo is 3:4 width:height. (The average size and dimensions for ebook covers in the Kobo store are 800:1224px width:height.) However covers in all dimensions will be rendered consistently across platforms. Content creators are advised to keep their cover images under 3MB. Larger covers will still render but will not improve the display of their content.

Covers should also be listed in the OPF metadata section. The metadata indicates the cover by pointing to the ID of the cover file in the manifest. Kobo uses this tag to identify which image to display as a thumbnail within user's libraries across platforms.

Ex. 
OPF metadata:

`<meta name=“cover” content=“cover-image”/>`

Manifest item listing:

`<item href="cover.jpg" id="cover-image" media-type="image/jpeg"/>`

**Cover images must be contained in their own XHTML files.** Kobo's eInk devices will activate the Fixed Layout reader for the XHTML file containing the cover image to optimize the display. As a result any text or images that have been placed in the same XHTML file as the cover will be displayed as Fixed Layout content. The user will be unable to resize the text and some of the content may not display on the screen at all. 
 
### Scalable Vector Graphics (SVG)
 
SVG is partially supported across Kobo platforms. Thorough testing is advised for ePubs with SVG, particularly for text rendering. Content creators are advised to use manifest fallbacks for SVG whenever possible. Refer to the support grid in this document or the test results for Kobo's reading platforms at [ePubtest.org] (http://www.epubtest.org).
 
### Table of Contents (ToC)
 
**For ePub 2.0.1**, Kobo reading platforms populate the ToC menu in the book with the ToC from the file toc.ncx (which is in navMap). However, if the toc.ncx is not present, the TOC menu is populated by the Spine listing in the OPF.
 
When an OPF-spine item is not listed in the TOC.ncx, the Kobo CMS will create a listing for it using the filename or the opening words from the section. This listing will be displayed to the user in the TOC Menu across all reading platforms. This process may be removed in a future release. ePubs that use a nav.html TOC will not be impacted. 
 
**For ePub 3.0**, Kobo platforms will read the ToC from the ToC table in the nav.html file. When a ToC table is not present, the next available table will be used. If the nav.html is not present, it will populate the ToC with the toc.ncx. If the toc.ncx is not present, it will populate the ToC with the spine listing in the OPF.
 
The hidden attribute can be used to prevent the ToC listing from appearing in the ePub body while still displaying in the ToC menu. ToC menus on Kobo platforms support nesting up to three elements deep.

Kobo does not require a specific naming convention for the .ncx or .html/.xhtml file, the content creator can name the file as they choose ([filename].ncx, [filename].html). Please note the file naming suggestions provided in the [OPF] (#OPF) section. 

### OPF
 
The Kobo CMS reads the external metadata provided by the publisher. So most fields in the metadata section of the OPF file are not read. The one exception is the <dc:identifier>. It should contain the eBook ISBN, also supplied in the external metadata. However, if this field does not contain the eBook ISBN, it must be in the ePub file name. Content creators are also advised that the <dc:identifier> in the OPF should be identical to the identifier in the .ncx file.
 
Kobo uses external metadata files to populate the various metadata fields on the Kobo website. The ISBN in the <dc: identifier> field in the OPF file matches the ePub to the external metadata entry. If there is no ISBN in the <dc: identifier> tab, Kobo looks for the ISBN in the ePub filename. The ISBN from the external metadata must match either the <dc: identifier> field or the ePub file name.
 
The OPF file can be named however the content creator chooses ([filename].opf), but please note the file naming conventions suggested below. 
 
**Content creators are advised to use [tags for manifest items](http://www.idpf.org/epub/30/spec/epub30-publications.html#sec-item-property-values)**, specifically the cover tag. Some of these are read across Kobo’s reading platforms and future developments will be able to take advantage of properly tagged items.
 
**Special characters and spaces should not be used** for file names within an ePub. This can result in naming inconsistencies with the items listed in the OPF manifest. File names containing non-alphanumeric characters are not fully supported, and their use may lead to undefined behaviour, which may be inconsistent across clients.

### CSS

**Background Colors**

Kobo recommends that publishers avoid specifying background colors in the CSS for reflowable ePubs. Background colors may make the content difficult to read when the user has selected the sepia or night modes or when reading on eInk devices. 

Ex.
`.c5 {
  background: #FF0000
  }`

**Small Caps**

In order to structure Small Caps that will display correctly on Kobo's reading platforms content creators must use the CSS property "font-variant".

Ex.
`p.sc {
   font-variant: small-caps;
}`

The property "font-size" is often used incorrectly to format Small Caps and can result in disproportionate text sizing depending on the app/device being used and the font settings chosen by the user. The impact is particularly noticeable when the value used for this property is set to "x-small" or "small". Content creators are also advised to use a font that contains Small Caps glyphs for optimal rendering.

**Inline Styling**

Kobo strongly advises against the use of inline styling for all content types (reflowable and Fixed Layout). Inline style elements may not be rendered as intended across Kobo's reading platforms. Styling elements should be contained within CSS.

For example, text should be formatted as follows: 

HTML:<br>
`<p class="text">Sample text.</p>`<br>
`<p class="text">Sample text, part two.</p>`<br>
CSS:<br>
`p.text {`
    `margin: 0;`
    `text-size: 10px;`
`}`

Not like this:

HTML:<br>
`<p style="margin: 0;text-size: 10px;">Sample text.</p>`<br>
`<p style="margin: 0;text-size: 10px;">Sample text, part two.</p>`<br>

**Viewport Height (vh)**

Kobo advises against using the CSS element 'vh' in reflowable content as it is not supported on all display engines and may result in text getting cut off or overlapping with other content. More conventional elements such as 'height' or 'max-height' are recommended. 

**Styling div tags**

Kobo advises against applying stlye elements in CSS to 'div' tags. These style elements will be applied to all content wrapped in 'div' tags throughout the ePub. In addition Kobo inserts 'div' tags during processing to enable user functionality (ex. text highlighting) and as a result any content contained within the added tags will inherit the styling applied in the CSS.

Ex.
`div {`<br>
    `font-weight: bold;`<br>
`}`

**Body Padding**

Kobo advises against adding padding to the 'body' class to accomodate background images. On the Kobo iOS platform this may result in the background image overlapping with the text.

Ex.
`body {`<br>
      `padding: 2em 1em 2em 70px !important;`<br>
      `background-image: url(logo-CR.png);`<br>
    `}`

![background sidebar image](https://github.com/kobolabs/epub-spec/blob/master/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202016-02-22%2014.51.00.png)

**Using em units for Margins**

Kobo advises against using em units to set text margins unless it's set to 1 or 2. When users on mobile devices select a large font this can make the content nearly unreadable. In this example the margins will always be 4x the size of the font selected and each line will only fit a few letters or words.

Ex.
From the HTML:
`<p class='quote_section'><b>This test will be unreadable on phones at large fonts sizes</b></p>`<br>
From the CSS:
`p.quote_section { margin: 0em 4em; text-align:justify; text-indent: 0em; }`<br>

**Page Breaks**

Page breaking CSS is only partially supported across Kobo's reading platforms. Work is underway to add support for all platforms in future releases. Current support across all platforms is as follows:

|Page Break Type| Windows | iOS | Android | EPD | KDA |
|---------------|---------|-----|---------|-----|-----|
| after:always  |    N    |  Y  |    Y    |  N  |  N  |
| after:auto    |    N    |  N  |    N    |  N  |  N  |
| after:avoid   |    N    |  Y  |    Y    |  N  |  N  |
| after:left    |    N    |  Y  |    Y    |  N  |  N  |
| after:right   |    N    |  Y  |    Y    |  N  |  N  |
| before:auto   |    N    |  N  |    N    |  N  |  N  |
| before:always |    N    |  Y  |    Y    |  N  |  N  |
| before:avoid  |    N    |  Y  |    Y    |  N  |  N  |
| before:left   |    N    |  Y  |    Y    |  N  |  N  |
| before:right  |    N    |  Y  |    Y    |  N  |  N  |
| inside:auto   |    N    |  N  |    N    |  N  |  N  |
| inside:avoid  |    N    |  N  |    N    |  N  |  N  |

**Setting Font Sizes**

Font size can be set in the CSS using the unit type em, px, pt or %. However % has been known to trigger bugs on Desktop and eInk that can restrict the users ability to change the font size or to reset the font size at the start of each chapter. Kobo advises that content creators set a base font size in px or pt or not set a base size at all (this will allow each platform to use it's default font size) then increase or decrease the font size throughout using em.

### Supported Fonts
 
TTF, OTF, and WOFF fonts are supported by all of our platforms. For a detailed breakdown of our font support by platform, check [EPUBTEST.org](http://epubtest.org/results). 

**Font customization options available to Kobo users** on each reading platform:
 
**Android:** Droid Sans Serif, Droid Serif.
 
**Desktop:** A-OTF Gothic MB101 Pr6N R, A-OTF Ryumin PR6N R-KL, Arial, Ariel Narrow, Arial Unicode MS, Calibri, Calibri Light, Cambria, Cambria Math, Constantia, DFKai-SB, Georgia, KaiTi, Lucida Sans, Palatino Linotype, Meiryo, Meiryo UI, MS Gothic, MS Mincho, MS PGothic, MS PMincho, SimHei, Times New Roman, Tahoma, Trebuchet MS.
 
**eInk:** Amasis, Avenir Next, Caecilia, Georgia, Gill Sans, Kobo Nickel, Malabar, Gothic, Ryumin, [Dyslexie](http://www.dyslexiefont.com), [OpenDyslexic](http://opendyslexic.org/) (the last two are optimized for readers with dyslexia).
 
**iOS:** Avenir, Baskerville, Cochin, Georgia, Helvetica, Optima, Palatino, Trebuchet, Verdana.
 
**Windows:** Cambria, Calibri, Georgia, SegoeUI, Times New Roman, Trebuchet MS, Verdana.

### Obfuscated Fonts Are Not Currently Supported by the Kobo CMS
Non-sideloaded titles with obfuscated fonts will display the reading platform’s default font instead of the intended font. As a result all Fixed Layout titles with obfuscated fonts are likely to fail QA. However, work is underway at Kobo to support obfuscated fonts and render these titles correctly.
DRM is applied to all ePubs sold through Kobo unless the account/publisher sending the content elects to have Kobo distribute their ePubs without DRM. As a result Kobo users will not be able to extract fonts from ePubs with DRM even when the embedded fonts are not obfuscated.

### Embedded Fonts Can Be Selected By Users 
When opening a new book, the font that displays is the one chosen by the user for their previous open book. For an embedded font, users can select “Document Default” or “Publisher Default” from the font options. The exception is FXL content for which users cannot choose their font. Fonts in FXL content are determined by the CSS in the ePub.

If the reading experience of a book requires that the embedded font be used, consider adding a note to the front matter. Instruct the user to select the “Document Default” font option. 

**To avoid text-positioning errors**, seriously consider embedding and specifying fonts in the CSS for all Fixed Layout ePubs. If fonts are not embedded and specified, the reading platform defaults to Times. Fixed Layout files that use the default font should be tested extensively on Kobo’s reading platforms.

**Content creators are advised against referencing fonts in the CSS that are not embedded in the ePub.** Kobo devices and devices that Kobo apps can be installed on will have specific fonts included. However the available fonts vary across these devices and there is no way to ensure that any one font will be available on the device chosen by the user. As a result the font styling in the CSS will not display as intended across multiple devices and platforms.

### All Fonts Used In Fixed Layout Content Must Be Embedded And Cannot be Modified

Emphasis cannot be added to embedded fonts for Fixed Layout content in the CSS. Reading systems cannot modify embedded fonts with bold or italics. Instead a seperate font file must me embedded for bold or italic versions of any fonts used. Files produced using InDesign will often add such modifiers to embedded fonts resulting in text that cannot be read on all Kobo platforms.

Ex. 
`CharOverride-22 { `</br>
`font-family:"Avenir Black",`</br>
`font-size:240px;`</br>
`font-style:normal;`</br>
`font-weight:800;`</br>
`}`

In this case a bold font should have been embedded instead of taking the original font and adding "font-weight:800". Alternatively the "font-weight" element could be removed entirely. The font would no longer appear bold but it would display consistently across all reading platforms. This can be detected most easily by sideloading content to the Kobo Desktop app where the resulting display issues are the most prominent.

### Languages Other Than English
 
When a user selects an available default font, Kobo reading platforms may not correctly render all glyphs within the script. So Content containing glyphs not present in Kobo’s default apps should be tested across platforms. Creators may want to embed a font that contains the glyphs used in their content to ensure it renders correctly.
 
Some glyphs do not render on most fonts. In cases where creators are unable to supply embedded fonts they can insert a note into the front matter of their content instructing users to select the font Georgia. It correctly renders the greatest set of scripts.
 
Kobo is currently working to add built-in fonts to the eInk and Android-reading platforms and render glyphs from all scripts correctly. The Desktop, iOS and Windows platforms already contain built-in fonts that will render glyphs from all scripts.

###Right to Left Page and Text Direction

Kobo has support for right-to-left language formatting in the following areas:
* Kobo supports the writing-mode CSS3 property and associated elements for vertical text layouts (LTR or RTL)
* Kobo supports the HTML5 dir attribute
* Kobo supports ruby text*
* * Kobo supports the OPF spine-level [page-progression-direction](http://www.idpf.org/epub/30/spec/epub30-publications.html#attrdef-spine-page-progression-direction) attribute for right-to-left page flow ex.
	`<spine toc="ncx" page-progression-direction="rtl">`<br>
		`<itemref idref="chapter1" />`<br>
		`<itemref idref="chapter2" />`<br>
		`<itemref idref="chapter3" />`<br>
	`</spine>`<br>
The "page-progression-direction" attribute was introduced as part of the ePub3 specification. However it can be used in both ePub2 and ePub3 files for Kobo and will pass through processing and display correctly on Kobo's reading platforms in spite of flags that ePub2 files will generate in ePubCheck.

### Footnotes/Endnotes Are Fully Supported Across Kobo Platforms
 
Footnotes and endnotes on the eInk (with the exception of the original Kobo reader and the Kobo Wi-Fi) and iOS platforms will display as a pop-up box containing the content being linked to. The pop-up boxes also contain links to the HTML sections containing the reference material. On iOS the footnote pop-up will render more than just plain text, including images, links and other content in the footnote or endnote. On the Desktop, Android and Windows platforms users will not see a pop-up but can simply follow the link to HTML section with the reference text.
 
It is strongly recommended that reference notes use the appropriate [ePub:type identifying attribute](http://www.idpf.org/epub/30/spec/epub30-contentdocs.html#sec-xhtml-content-type-attribute) for footnotes and endnotes (note: this markup is only valid in ePub 3 files and cannot be used in ePub3). This attribute is currently supported on Kobo's iOS platform and its use is the best way to ensure that footnotes and endnotes will display as intended on iOS as well as future releases on other platforms. All links using the footnote or endnote attribute will display within a pop-up on Kobo's iOS platform. Ex.
`<span id="fn0005fn" epub:type="footnote">Text linking to footnote or endnote.</span>`

**Warning: Hyperlinked content not using the epub:type attribute footnote or endnote will display as a pop-up on Kobo's iOS and eInk platforms in cases where all of the following criteria are met.**

1) The link references a location in the ePub and also references a specific node within the HTML. Ex.
<br>`<a href=“chapter.html#uniqueID”>link text</a>`<br>
Where chapter.html is a file within this epub and where uniqueID is the id of a node within that html document.

2) The content in the node is nine charcters or more once stripped of the HTML tags. Ex.
<br>`<p id="uniqueID">123456789</p>`

3) The node being linked to is less than or equal to 5000 characters.

4) The location being linked to comes after the location being linked from. Ex. A reference in Chapter 2 links to a location at the end of the file titled Endnotes or a reference at the beginning of Chapter 2 links to a location at the end of Chapter 2.

### Fixed Layout (FXL) Support
 
Kobo supports the [official ePub3 FXL spec](http://www.idpf.org/epub/fxl/). This includes such features as [Right-to-Left Reading](http://www.idpf.org/epub/30/spec/epub30-publications.html#attrdef-spine-page-progression-direction), SMIL/Read Along, and various rendition-spread options. The [rendition:layout property](http://www.idpf.org/epub/fxl/#property-layout) in the OPF determines the layout of the content and is read by all of Kobo’s platforms.
 
Kobo platforms also read the field <option name=”fixed-layout”>true/false</option> to identify whether ePubs should be rendered as FXL. The file containing this field is usually titled com.kobobooks.display-options.xml and can be found in the META-INF directory of the ePub. This file is not required for ePub3 FXL content. 

All five values in the [rendition:spread property](http://www.idpf.org/epub/fxl/#property-spread) are on the Android, Desktop and eInk reading platforms. The iOS platform supports the properties "Both", "None" and "Auto" but not "Portrait" or "Landscape". The Windows platform supports the properties "None" and "Auto" but not "Both", "Portrait" or "Landscape". Rendition-spread properties are only read at the book level for all reading platforms. Future versions of Kobo’s reading platforms may read the rendition:spread and rendition:layout properties at the spine level.
 
**Pinch and zoom gestures** are available on the Android, iOS, and Windows reading platforms. The zoom option is available in the reading menu of eInk devices. The Kobo Desktop App supports three zoom options: Zoom Slider, Double-click to zoom and Scroll to zoom. The zoom slider is incorporated into the navigation bar so that users can adjust it to zoom in and out. Alternatively, users can to zoom in by double-clicking anywhere on the page or adjust the zoom by scrolling  up and down with a mouse while holding down the Ctrl (PC) or Command (Mac) key.

**Starting a Fixed Layout Book with a left spread will throw off the page sequence on iOS**

The Kobo iOS app will always display the first page centered and as it's own spread. As a result if a Fixed Layout book is formatted as follows it will display the first item as the cover then the second as the left side of the first fill spread and the third as the right side of the first full spread. This will alter the sequence for the entire book, making all right spreads fall on the left side and vice versa. To avoid triggering this display issue simply do not indicate a page spread property for the first item and have your second item start as a left side spread.

Ex. </br>
  `<spine toc="ncx">`</br>
    `<itemref idref="page_000001.xhtml" properties="page-spread-left"/> [blank page]`</br>
    `<itemref idref="page_000002.xhtml" properties="page-spread-right"/> [cover image]`</br>
    `<itemref idref="page_000003.xhtml" properties="page-spread-left"/>`</br>
    `<itemref idref="page_000004.xhtml" properties="page-spread-right"/>`</br>
    `<itemref idref="page_000005.xhtml" properties="page-spread-left"/>`</br>

**Kobo strongly advises against the following when formatting Fixed Layout content:**

* Text boxes with inline styling. This may result in inconsistent rendering across platforms, resulting in text overlap or incorrect positioning.
 
* The use of images where the width or height (in pixels) exceed the dimensions of the viewport. ePubs containing images that exceed the viewport dimensions may not render correctly on the eInk platform.

* The use of negative positioning when placing text, images or other content in CSS. Ex.

`.li` </br>
`{ text-align: justify;`</br>
`padding: 0;`</br>
`margin: 0;`</br>
`word-spacing: -15px;`</br>
`}`</br>

**Kobo Advises Against Overuse of Fixed Layout**

Content creators are advised against producing Fixed Layout ePubs solely for the purpose of reproducing a print layout. Text cannot be resized by users while reading Fixed Layout content and as a result small text can only be read by zooming in. This can greatly diminish the reading experience particularly on eInk devices, smartphones and Desktop applications. Fixed Layout serves comics, children's books and other categories well but is not an ideal format for text heavy content that could be displayed as reflowable content. Furthermore Fixed Layout ePubs require more in depth testing prior to distribution to ensure that they display correctly across multiple reading platforms.

### Kobo Supports SMIL
 
[SMIL (Synchronized Multimedia Integration Language)](http://www.idpf.org/epub/30/spec/epub30-mediaoverlays.html#sec-smil-smil-elem) is supported for FXL titles on Android and iOS. Audio files must be encoded using Apple iTunes AAC-LC mp4-v2 codec, 256 kbps.
 
Note: the Kobo Android platform **does not currently support**:

* Non-Linear playback
* Text highlighting for SVG text
* Specifying time in microseconds ex. clipBegin="0.001s" clipEnd="10.001s". This may cause the audio to stop playing or not start playing at all.
 
When the rendition:spread property is set to “none” or “auto”, Android displays a full spread in FXL Read Along content in landscape.
 
Custom text colors for highlighting are not currently supported on Android. However, custom text colors for highlighting is possible on iOS. The iOS app uses the CSS class ‘kobo-smil-highlight’ to color highlighted text. So, by adding that class to the CSS plus a color declaration, the color of the highlighted text on the app can be customized.

**SMIL for reflowable content** is supported on iOS but is not supported on the Android, Desktop or Windows platforms.

### Image-Based FXL Reader
 
The Kobo Android and iOS platforms will render FXL ePubs that meet certain criteria with an image-based Fixed Layout reader. This reader features significantly faster panning, zooming, and page-turns than the standard one. Designed to enhance the reading experience of comics, it works for any FXL ePubs composed entirely of images.
 
**ePubs that meet the following criteria will be displayed with the image-based reader on Kobo’s iOS and Android platforms**:

1. The content is Fixed Layout.
2. The ePub does not contain SMIL content.
3. An image must be available for each spine item. Spine items are inspected for images using these rules — and each spine item must contain one of the following formats:
<ul>
<li>a. either a non-SVG image (e.g. PNG)</li>
<li>b. or an SVG image with a non-SVG image fallback provided in the manifest. In this case, the fallback image is used in the comics renderer</li>
<li>c. or an HTML file which falls under one of the following categories:
<ul>
<li>i. either it contains a single ‘img’ tag which references an image. In this case, this image will be used</li>
<li>ii. or it contains a svg definition with an ‘image’ child tag referencing an image. In this case, the referenced image will be used. NB: embedded object tags (‘object’), which may include an SVG image in the ‘data’ attribute, do not fall into this category</li>
<li>iii. or an HTML page which contains no child elements under ‘body’. This item will be rendered as a blank white page.</li></ul></li></ul>
4. The same image cannot appear twice in a row. If two consecutive pages refer to the same image, the platform will assume that CSS styling is repositioning the image, which is not supported by the image-based FXL reader.
 
For example, a file that lists spine items, manifest items, and contains nothing but an image in the HTML body will trigger the image-based renderer.
 
First spine item:<br>
`<spine page-progression-direction="ltr" toc="ncx">`<br>
`<itemref idref="page0-xhtml" linear="yes"/>`

Matching item in manifest:<br>
`<item id="page0-xhtml" href="contents/Page00.xhtml" media-type="application/xhtml+xml"/>`
 
HTML body for item:<br>
`<body>`<br>
`<div id="layer0">`<br>
`<image width="1076" height="1394" xlink:href="../images/Image01-1-0.jpg"/>`<br>
`</div>`<br>
`</body>`
 
If images are set using the [background property](http://www.w3.org/TR/CSS21/colors.html#propdef-background) of elements the platform will fall back to using the default reader.
 
On Android, if the image is determined to be twice as large as the screen in any dimension, a low-res version of the image loads when the user turns a page. Within a second, the high-res version replaces the original image. This optimization prevents memory issues when users quickly flip through pages. The low-res image might appear slightly blurry or soft compared to the final hi-res image.

### Multimedia Support / Media Overlays 
 
Testing across platforms for ePubs with multimedia and other media overlays is recommended.
 
Embedded audio and video is currently supported on Kobo’s iOS and Android platforms for all content. 
 
Windows does not currently support embedded audio and video. Kobo eInk devices and the desktop app do not support embedded audio and video either but will display any content included as a fallback using the [switch element](http://www.idpf.org/epub/30/spec/epub30-contentdocs.html#elemdef-switch) display instead.

**Autoplay Functionality is Not Currently Supported**

Kobo's platforms do not currently support autoplay functionality for embedded media. Elements using this tag will display but will not begin playback without user interaction.

Ex. <br>
`<audio class="myaudio" src="sounds/audio.mp3" autoplay="autoplay">Sample text.</audio>`
 
**Extensive Testing is Strongly Recommended For All Interactive Content**

For content with interactive features (ex. pop-ups, buttons that trigger media, scrolling windows within Fixed-Layout ePubs, text input boxes) it is strongly recommended that content creators test by sideloading to both Kobo's iOS and Android platforms to ensure that all features work as intended. Furthermore this content should be tested by sideloading on Kobo's Windows and Desktop platforms to verify that the lack of interactivity support does not make the content unreadable to the user. Ideally these ePubs will be sent with metadata where the synopsis indicates that features within the content may not work on all platforms.

Any content creators who cannot test each interactive title on both Kobo's Android and iOS apps are advised to not distribute such titles to Kobo at present.
 
### JavaScript Support
 
Kobo’s Android and iOS platforms support JavaScript for Fixed Layout and reflowable ePubs, but it is recommended not to use JavaScript in reflowable content in ways that may alter the layout of the book. Kobo’s eInk and Desktop platforms have limited support for JavaScript, and do not support interactive JavaScript elements. ePubs with JavaScript should contain fallback statements. This way, platforms that do not support JavaScript can still produce a coherent reading experience. Thorough testing on all platforms is strongly recommended to ensure that fallback as well as JavaScript content renders correctly.

**The navigator.epubReadingSystem Property** 

Note that <a href="http://www.idpf.org/epub/30/spec/epub30-contentdocs.html#app-ers-syntax">navigator.epubReadingSystem property</a> is only supported on Kobo's Desktop and eInk platforms and is not presently supported on iOS, Android or Windows. As a result ePubs that need to query information on three of Kobo's five reading platforms. Any ePubs that depend on this functionality to present readable content will not pass content QA. 

**Disabling Menu Activation for Interactive Elements**

Taps in book content (on elements other than links) are passed up to the Kobo reading apps in order to trigger menus and other reading system interactions. To avoid having your interactive elements trigger unrelated reading system functionality JavaScript files must contain event listeners for both _click_ and _touchend_ (or _touchstart_) events, and both listener functions must call [preventDefault()](http://www.w3schools.com/jquery/event_preventdefault.asp) on both _click_ and _touchend_ (or _touchstart_, if you’d prefer) events. Any interactive logic will need to be implemented in the touch handler, rather than the click handler, as in the example below:
<pre><code>exampleElement.addEventListener('click', handleClick, false);
exampleElement.addEventListener('touchend', handleTouch, false);

function handleClick(event) {
	event.preventDefault();
}

function handleTouch(event) {
	exampleElement.style.background="red";
	event.preventDefault();
}
</code></pre>
 
### MathML is Supported on iOS, elnk, and Desktop platforms
 
Please note that [MathML](http://www.idpf.org/epub/30/spec/epub30-contentdocs.html#sec-xhtml-mathml) is not presently supported on the Kobo Android platform. At present content creators are encouraged to either include a note to indicate that the content is not optimized for Android and devices, or else uses (rather than MathML) for the mathematical content. The website https://www.mathmlcloud.org/ is recommended for converting MathML into various outputs for inclusing in your ePubs.

### Fallback Statements
 
Any items listed in the manifest that are not [standard ePub Content Documents](http://www.idpf.org/epub/30/spec/epub30-publications.html#gloss-content-document-epub) should be accompanied by fallback items. Extensive testing should be done across platforms whenever including non-core items in an ePub. More on the IDPF specification on manifest fallbacks can be found [here](http://www.idpf.org/epub/30/spec/epub30-publications.html#sec-fallback-processing-flow-manifest).

Ex.<br>
`<manifest>`<br>
  `<item id="xpgt1" href="styling/noncorestyling.xpgt" media-type="application/vnd.adobe-page-template+xml" fallback="css"/>`<br>
  `<item id="css" href="styling/content.css" media-type="text/css"/>`<br>
`</manifest>`<br>

When embedding audio and video Kobo recommends using intrinsic fallbacks so that users reading on platforms that do not support embedded media (ex. eInk) can be directed to other platforms if they wish to access the content. More on IDPF specification on intrinsic fallbacks can be found [here](http://www.idpf.org/epub/30/spec/epub30-publications.html#sec-foreign-restrictions).

Ex.<br>
`<audio controls="">`<br>
  ` <source src="embeddedaudio.mp4">`<br>
  ` <p>The device you are reading on cannot play audio content but you can access the media in this book by opening it on your phone or tablet.</p>`<br>
`</audio>`

### ePub Previews 
 
Publishers can set the amount of content they make available in previews. They use their metadata feed or work with Kobo’s Publisher Operations team to customize their account settings.
 
**On the account level**, previews are set to display 5% of the ePub’s content by default. Previews can be turned on or off. The maximum percentage that accounts can be set to is 25%.
 
**On the product level**, the default is 5%. Publishers can set preview percentages for individual titles. They can use the Kobo Excel metadata template or ONIX 3.0 with the tags EpubUsageType, EpubUsageStatus or EpubUsageLimit. Previews can be set between 0% and 25%.
 
Publishers can also upload custom previews by using the naming convention ISBN_preview.epub in the preview files they distribute.
 
### Tables 
 
Sometimes tables wider than four columns may not be readable in reflowable ePub files, particularly on eInk devices. Content producers adding tables with more than four columns are advised to test their content on all Kobo reading platforms. Likewise, when HTML tables do not render as intended, they can reformat or capture the tables as high-resolution images.
 
### Limitations and Maximums 
 
Kobo recommends the following limits for ePub and ePub component sizes. Files exceeding these limits should still to load to the Kobo store and be accessible on all reading platforms but will take longer to download to users’ devices and will take up more memory. To ensure optimal performance content creators are advised against producing files that exceed these limits.
 
* 5 MB/image in FXL and Reflowable ePubs
* 10 MB of embedded content/each HTML file in an ePub
* 3 800 000 pixels/viewport or ~1950x1950 in FXL ePubs 
* 1 GB/ePub
 
### Support Grid

The following table lists features supported by at least one Kobo platform but not uniformly supported across all platforms. Features not listed here are either supported across all platforms or not supported on any platforms.

| Platform  | MathML | SMIL | JavaScript | CSS Animations | Audio/Video |
|-----------|--------|------|------------|----------------|-------------|
| Android   | N      | Y    | Y          | Y              | Y           |
| Desktop   | Y      | N    | N          | Y              | N           |
| eInk      | Y      | N    | N          | Y              | N           |
| iOS       | Y      | Y    | Y          | Y              | Y           |
| Windows   | N      | N    | N          | N              | N           |

### Common QA Failure Issues

Kobo routinely reviews content and will remove titles from sale when display issues have a significant and negative impact on the reading experience. In these cases a report will be sent to the account contacts indicating which reading platforms the issues were detected on and why it was removed from sale. Upon request Kobo can perform further testing, provide more feedback and sync to content to a Kobo user account belonging to the distributor or creator of the ePub file in question. Two key methods for revising failed content are side-loading and running ePubCheck.

**Side-loading**

Sideloading content for testing purposes will allow you to see the issue first hand (with the exception of ePubs with obfuscated fonts which will display correctly when side-loaded but not when loaded into the Kobo store). This can also be used after fixes are applied, to verify that content is displaying as intended. Instructions for sideloading ePubs to each of the different platforms can be found [here](https://github.com/kobolabs/epub-spec#sideloading-for-testing-purposes).

**Running ePubCheck**

Using an [ePub validator](http://validator.idpf.org/) will help detect errors within the ePub. In some cases Kobo will be unable to investigate failed content until the file passes validation without raising any flags. There are ePubs that will raise flags in ePubCheck that will sucsessfully load and display on Kobo as well as files that will pass ePubCheck and still fail to display correctly on Kobo's platforms. However files that pass ePubCheck are always less likely to produce display issues and those that do are much easier to diagnose. When display issues are produced by valid ePubs that display correctly on other reading platforms Kobo will log bugs and attempt to resolve them for future releases.

### Pixelated or Low Resolution Images

Kobo often receives reports from customers that images in ePubs are blurry and contain text or images that are not legible.

To revise ePubs with this issue:
* Embed higher resolution images and test via sideloading. Instructions for sideloading can be found [here](https://github.com/kobolabs/epub-spec#sideloading-for-testing-purposes). There's no miniumum size or dimension required for images but if the image does not appear pixelated on an iPad or Android tablet it should pass content QA. You can  double tap to expand images in reflowable content to full screen on Android and iOS for review.
* When you are satisfied with the image quality, please send in the revised file and let us know that it is available for additional QA testing.
* If you have tried replacing the images and the issue still exists contact the Content QA team for additional feedback.

### Missing Images

Kobo often receives ePubs where images are missing or fail to display within the ePub on one or more reading platforms.

To revise ePubs with this issue:
* If images are failing to display on all platforms:
	* Check that the image is being correctly referenced throughout the HTML, OPF and file name. Sometimes there is a slight discrepancy between the link and the name of the image; this results in the image link being broken. There may also be special characters or spaces in the filename resulting in a mismatch between how the file is named in the OPF. Reading systems may fail to identify images in these cases. Ex. The image in the ePub could be called “image with spaces.jpg” and would be labelled “`image&nbsp;with&nbsp;spaces.jpg`” in the OPF file.
* If images are failing to display specifically on the desktop platform:
	* Check the code for the use of negatively positioned images.
	* Check to see if you are scaling images. If you are using transforms to shrink/expand the image iy may not display on the Desktop app and eInk devices at all. This issue is expanded on [here](https://github.com/kobolabs/epub-spec#image-formatting)
* If you have tried revising the images and the issue still exists contact the Content QA team for additional feedback.

### Blocks Appearing in Place of Text on Desktop and eInk Platforms

Applying style modifications (ex: bolding, italicizing, etc) to embedded fonts rather than embedding separate modified versions of those fonts will result in a display on Desktop and eInk where the text expands to the point where it is not legible. [This section above](https://github.com/kobolabs/epub-spec#all-fonts-used-in-fixed-layout-content-must-be-embedded-and-cannot-be-modified) covers this display issue in greater detail.

To revise ePubs with this issue:
* Embed actual styled fonts (ex: bold or italic fonts) in place of modifying fonts in the CSS.
* Test via sideloading to the desktop platform to ensure that the text is displaying properly. Instructions for sideloading can be found [here](https://github.com/kobolabs/epub-spec#sideloading-for-testing-purposes).
* If the fonts are displaying as intended, please send in the revised file and let us know that it is available for additional QA testing.
* If you cannot get the fonts to display correctly on Desktop and eInk contact the Content QA team for additional feedback.

### Font Obfuscation

Kobo does not currently support [font obfuscation](https://github.com/kobolabs/epub-spec#obfuscated-fonts-are-not-currently-supported-by-the-kobo-cms) and will fail Fixed Layout content when the fonts have been encrypted. When loaded to the store these titles will have revert to system fonts instead of the fonts that are embedded and the text will not display as designed.

To revise ePubs with this issue:
*Embed versions of the fonts that are not encrypted, or replace the fonts with new non-encrypted fonts. Removing the encryption key (the encryption.xml file) will not fix the file as the fonts will still be encrypted. 
* Extract the ePub, open the font folder and try to open the font file. If the font can’t be opened our apps and devices won’t be able to read the fonts either.
* If needed, revise the layout of the book to accommodate the new fonts.
[Sideload the ePub](https://github.com/kobolabs/epub-spec#sideloading-for-testing-purposes) to various platforms and test that the text displays as intended. 
* If the fonts are displaying as intended send in the revised file for retesting.
* If the fonts cannot be replaced and must be obfuscated then simply confirm that you will not be revising the content. Kobo will have the content retested and activated (if it passes QA) when support for obfuscated fonts is added.
* If you cannot revise the file contact the Content QA team for additional feedback.

### Text Spacing and Overlap Issues

Issues with text spacing and overlap in Fixed Layout ePubs are often caused by strict styling specifications. Kobo strongly recommends that styling be done at the paragraph level (as opposed to placing each character or word individually) and that styling elements be contained within the CSS (as opposed to the XHTML files). The more styling present in the .xhtml files and the more rigidly the text is styled the less likely it is that the content will display as designed across all Kobo reading platforms.

To revise ePubs with this issue:
* If your file is using inline styling (or even styling individual words or characters), consider styling your content at the paragraph level. If your style elements are contained within the .xhtml files, consider placing the styling within the CSS. An example and a more detailed explanation can be found [here](https://github.com/kobolabs/epub-spec#css).
* Increase the width allowance of the line/paragraph and build in extra space to accommodate slight display discrepancies between Kobo reading platoforms and the devices they are available on.
* Side-load the ePub to various platforms and test that the text displays as intended. Instructions for side-loading content can be found here: https://github.com/kobolabs/epub-spec#sideloading-for-testing-purposes
* If the text is displaying as intended send in the revised file for additional QA testing.
* If you cannot revise the text layout contact the Content QA team for additional feedback.

### Viewport Issues

Fixed Layout content will fail QA in instances where the page content does not fit into or exceeds the window/screen. On devices this will manifest itself as extra white space on the screen or it appearing as though a zoom has been applied. This is the result of inconsistencies between the viewport specified in the XHTML, CSS or in the dimensions of the images being referenced on the pages.

To revise ePubs with this issue:
* Ensure that the viewport listed in all the CSS and XHTML files is the same.
* Check to see if the image dimensions (if there is one background image for each page) matches the dimensions of the viewport. The image size does not have to match the viewport but the width:height ratio does. Ex. The image can be 100px by 200px and the viewport could be 200px by 400px.
* [Side-load](https://github.com/kobolabs/epub-spec#sideloading-for-testing-purposes) the ePub to various platforms and make sure that there is no extra space, that the whole page displays and that the left and right sides of the pages match up if the book is designed to be displayed in two page spreads.
* If you cannot correct the viewports contact the Content QA team for additional feedback.

### Read-Along issues

Common issues flagged in QA for books with Read-Along audio include audio stuttering, audio getting cut off before all the text on the page has been read, reading text that is not on the current page or not playing the audio track at all. More on Kobo's support of Read-Along can be found [here](https://github.com/kobolabs/epub-spec#multimedia-support--media-overlays).

To revise ePubs with these issues:
* Ensure that you are using the SMIL format to enable Read-Along and that it conforms with the [specification](https://www.w3.org/TR/SMIL/)
* Check the mimetype for your SMIL files in the OPF manifest. It should be application/smil+xml.
* Play the embedded audio file and compare it to the times listed in the .smil files. The times listed in the .smil files should match the audio you want to hear for that page in the audio file.
* If a page references multiple audio files or if the SMIL file references out of sequence points in the audio file (ex. it reads seconds 2-8, then 20-24, then 10-13) this may result in performance issues across reading platforms. You can improve performance by having each page only refer to one audio file and having that sequence of the audio match the sequence of the text being read.
* [Side-load](https://github.com/kobolabs/epub-spec#sideloading-for-testing-purposes) the ePub to various platforms and test that the audio plays as intended.
* If you cannot resolve the playback issues contact the Content QA team for additional feedback.

### Audio Video Issues on Android and iOS Platforms 

Kobo often receives content with embedded audio that does not work on on or both of our iOS and Android platoforms (the criteria for activating such content is that is pass QA on both). This is usually either because the content has not been designed and tested for more than one reading platform or because the media, codecs, HTML or mimetypes are not compatible with one or both of the Android and iOS devices at all (ie. even outside of the Kobo app).

To revise ePubs with these issues:
* Ensure that the audio/video components are compatible with iOS and Android devices independent of the Kobo app by extracting the audio or video file and opening it in an app that will play the content. If it does not play the problem is likely the case that the file itself is not compatible with the Android or iOS platform.
* Make sure you are using the [correct mimetype](http://www.iana.org/assignments/media-types/media-types.xhtml) for the audio/video file you’ve embedded.
* Unzip the ePub and open the page containing the media in Chrome and Safari. If it doesn’t work on Safari it will not likely work on the Kobo iOS app and if it does not work in Chrome it will not likely work on the Kobo Android app. The display engines will not always be the same version but they will be very similiar. If the media plays in the browser and when opened in a media app on the device but not the Kobo app we will log a ticket in order to support the media for a future release.
* Check the media controls. If the reading system has been allowed to use it’s default media controls it will decrease the likelihood that the media will not play. If Javascript is in use try to remove it without breaking the intended display of the content.
* If you unable to get the media to play on both platforms contact the Content QA team for additional feedback.

### Still have questions? 
 
Learn more about Kobo’s ePub support at [epubtest.org](http://epubtest.org/). It’s categorized into required and optional features. 

If you encounter any rendering issues you can bring them to our attention at renderingissues@kobo.com. Please provide as much detail as possible, including app version, device, and screenshots if possible. Any comments or concerns about the documentation above can be submitted directly via Github comments. Immediate responses to all emails and comments cannot be guaranteed but all feedback related to documentation and content rendering is appreciated.

If you are already configured as a publisher or distributor with Kobo and have a questions concerning content management (metadata or ePub uploads, pricing, pre-orders, etc.) you can follow up with your contact on the Publisher Operations team.

If you are a small publisher or a self-published author and would like to sell your content through Kobo you can do so through [Kobo Writing Life](http://www.kobo.com/writinglife).
