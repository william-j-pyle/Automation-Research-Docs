.i
-------------------
4 - nextion rec type?
4 - 0
4 - header size
2 - width
2 - height
4 - size of image
4 - 0
-------------------

Sorry for the late reply, but I had to do research on why the pictures become so big in file size when you import them on Nextion.

The accepted picture types to import are *.jpg, *.png, non animated *.gif and *.bmp files.

When importing a picture, the picture is converted into the 565 16 bit color format used by Nextion.

In Basic and Enhanced models: Nextion is not a graphics card, as such transparency and in picture animation is not supported.

In native 16-bit color, picture, resources consume 16 bits per pixel, or width x height x 2 bytes.

In Intelligent models: Nextion now supports transparency and image compression allowing more picture resources for the same space, the 2 bytes per pixel formula does not apply.

Also, I wanted to see if this was true, so I tested it to prove it.

For Basic and Enhanced models:

Resolution	.tft file size	format/image size	imported image size	.tft after import
480x320:	277 KB	.png / 196 KB	307,224 B	605,536 B
480x320:	277 KB	.jpg / 12 KB	307,224 B	605,536 B

800x480:	277 KB	.png / 351 KB	768,024 B	1064,288 B
800x480:	277 KB	.jpg / 22 KB	768,024 B	1064,288 B
And for Intelligent models:

Resolution	.tft file size	format/image size	imported image size	.tft after import
800x480:	538 KB	.png / 351 KB	138,919 B	669,980 B
800x480:	538 KB	.jpg / 22 KB	88,630 B	669,980 B
Conclusion:
Basic and Enhanced models no matter the picture format and size, the final size of the imported image, will be the same, following the rule: width x height x 2 bytes. For example: 8004802=768,000B.

For the Intelligent models, the file format does not matter again, as the final .tft file size will be the same, following Nextion’s image compression.



RGB565 requires only 16 (5+6+5) bits/2 bytes and is commonly used with embedded screens. It provides 5 bits for Red and Blue and 6 bits for Green. Providing 5 bits for 2 colors and 6 bits for another seems asymmetric but storing and transmitting something which cannot nicely be packed in bytes would be complicated.

To convert to 565

- convert input.png -define bmp:subtype=RGB565 output.bmp
    - reported that gradients are edgy
- ffmpeg -i input.png -pix_fmt rgb565 output.bmp
    - report to have clean gradients


