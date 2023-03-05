# /c/development/tools/ffmpeg/bin/ffmpeg -i 0.is.jpg -pix_fmt rgb565 output.bmp

# BITMAP-14
Magic
	2 Bytes		String "BM"
ImageSize
	4 Bytes		UInt32
Reserved
	2 Bytes		Byte(2) - App Specific - NULL
Reserved
	2 Bytes		Byte(2) - App Specific - NULL
Offset            	
	4 Bytes		UInt32
# BITMAPINFOHEADER - 40
HeaderSize
	4 Bytes		UInt32
ImageWidth
	4 Bytes		UInt32
ImageHeight
	4 Bytes		UInt32
ColorPlanes
	2 Bytes		Int16 - Always 1
BitsPerPixel
	2 Bytes		Int16 - For 565 its 16
Compression
	4 Bytes		UInt32 - See lookup table - 3
RawImageSize
	4 Bytes		UInt32 - 0 for BI_RGB
HorizontalResolution
	4 Bytes		UInt32
VerticalResolution
	4 Bytes		UInt32
ColorsInPallete
	4 Bytes		UInt32
ColorsUsed
	4 Bytes		UInt32
# BITMAPINFOHEADER2 - 24
ResolutionUnit
	2 Bytes		UInt16 - Lookup
Padding
	2 Bytes		UInt16 - Ignored and should be zero
ENumFillDirection
	2 Bytes		UInt16 - 0=L->R/B->T, in our sample its 224
HalfToneAlgorithm
	2 Bytes
HalfToneParm1
	4 Bytes		UInt32
HalfToneParm2
	4 Bytes		UInt32
ENumColorEncoding
	4 Bytes		UInt32
Reserved
	4 Bytes		UInt32

