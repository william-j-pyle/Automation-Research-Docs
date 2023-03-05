# HMI-File-Format

## Git Lab Projects
https://github.com/UNUF/TFTTool
https://github.com/MMMZZZZ/Random-Stuff/tree/eea7398335ff6a92c16227dbe911bf3e18e9728d/Nextion%20HSV%20Test
https://github.com/UNUF/nxt-doc
https://github.com/UNUF/nextion-tft-uploader
https://github.com/UNUF/Nexus
https://github.com/UNUF/TFTTool
https://github.com/UNUF/nextion-font-editor

## Nice Images
https://tech.scargill.net/coding-the-nextion/ 


> https://unofficialnextion.com/t/crc-collisions-and-related-experiments/1222
> https://unofficialnextion.com/t/ideas-for-nextion-color-picker-control/891/11
> https://unofficialnextion.com/t/splash-screen-fading-in/294
> https://unofficialnextion.com/t/generating-crc-wrong/986
> https://wiki.iteadstudio.com/index.php?title=Nextion_Instruction_Set&oldid#Nextion_HMI:_System_Variables_List


# Code Examples
https://nextion.tech/2022/06/13/professional-gui-popup-windows/
https://nextion.tech/2022/04/11/the-sunday-blog-circular-controls-part-1/
https://nextion.tech/2022/04/18/the-sunday-blog-circular-controls-part-2/
https://nextion.tech/2022/03/21/the-sunday-blog-dynamic-data-display-using-arrays-or-kind-of/
https://nextion.tech/2021/10/18/the-sunday-blog-graphics-programming-once-more-the-moving-window-technique-explained/
https://nextion.tech/2021/07/19/the-sunday-blog-optimized-coding-an-example/
https://nextion.tech/2021/06/14/the-sunday-blog-advanced-programming-techniques-input-validation/


# Custom Components
https://nextion.tech/2020/10/12/the-sunday-blog-understanding-and-customizing-hmi-components-part-8-extend-an-existing-component-the-animated-progress-bar/
https://nextion.tech/2020/10/05/the-sunday-blog-understanding-and-customizing-hmi-components-part-7-design-a-new-component-from-scratch-the-bar-graph-display/
https://nextion.tech/2020/09/28/the-sunday-blog-understanding-and-customizing-hmi-components-part-6-the-timer-component-and-animated-gifs/
https://nextion.tech/2020/09/21/the-sunday-blog-understanding-and-customizing-hmi-components-part-5-custom-switches-and-true-radio-buttons/
https://nextion.tech/2020/09/14/the-sunday-blog-understanding-and-customizing-hmi-components-part-4-the-picture-component-and-animations/
https://nextion.tech/2020/08/31/the-sunday-blog-understanding-and-customizing-hmi-components-part-3-color-encoding-sliders-subroutines-and-a-hue-control/
https://nextion.tech/2020/08/24/the-sunday-blog-understanding-and-customizing-hmi-components-part-2-a-project-without-visible-components/
https://nextion.tech/2020/08/17/the-sunday-blog-understanding-and-customizing-hmi-components-part-1-introduction/

# Math
https://nextion.tech/2020/08/02/the-sunday-blog-boost-your-hmi-with-advanced-mathematics-part-5-harmonic-motion/
https://nextion.tech/2020/07/26/the-sunday-blog-boost-your-hmi-with-advanced-mathematics-part-4-trigonometry/
https://nextion.tech/2020/07/20/the-sunday-blog-boost-your-hmi-with-advanced-mathematics-part-3-drawing-curves/
https://nextion.tech/2020/07/13/the-sunday-blog-boost-your-hmi-with-advanced-mathematics-part-2-the-binary-fixed-point-format/
https://nextion.tech/2020/07/05/the-sunday-blog-boost-your-hmi-with-advanced-mathematics-part-1-introduction/

# Dishwasher UI
https://nextion.tech/2020/06/28/the-sunday-blog-hmi-cybernetics-and-the-steam-engine-part-7-didactic-code/
https://nextion.tech/2020/06/22/the-sunday-blog-hmi-cybernetics-and-the-steam-engine-part-6-professional-graphics/
https://nextion.tech/2020/06/15/the-sunday-blog-hmi-cybernetics-and-the-steam-engine-part-5-well-thought-out-and-efficient-hmi-code/
https://nextion.tech/2020/06/08/the-sunday-blog-hmi-cybernetics-and-the-steam-engine-part-4-theory-and-practice/
https://nextion.tech/2020/06/01/the-sunday-blog-hmi-cybernetics-and-the-steam-engine-part-3-embedded-development-in-detail/
https://nextion.tech/2020/05/25/the-sunday-blog-hmi-cybernetics-and-the-steam-engine-part-2-it-becomes-very-complex/
https://nextion.tech/2020/05/18/the-sunday-blog-hmi-cybernetics-and-the-steam-engine-part-1-how-it-all-began/



## Nextion external control of everything
https://github.com/sstaub/NextionX2




UInt32 - Are stored Little Endian
String - NULL padded to specified length
Boolean- 0-False 1-True

## Header

> Offset: 0000:0000

 | Bytes              | Field                        | Type   | Description |
 | ------------------ | :--------------------------- | ------ | ----------- |
 | 4                  | ObjectCount                  | UInt32 | Total Objects in File            |
 | 28 * `ObjectCount` | ObjectReferences(ObjectCount) | Array  | Array of ObjectReference Objects            |
 | 4                  | Crc                          | UInt32 |             |

## ObjectReference

 | Bytes | Field     | Type    | Description |
 | ----- | :-------- | ------- | ----------- |
 | 16    | Name      | String  | Null terminated String, when Deleted, 1st Byte is null            |
 | 4     | Offset    | UInt32  | Abosolute Offset to Object            |
 | 4     | Size      | UInt32  | Object Size in Bytes            |
 | 4     | IsDeleted | UInt32  | Boolean 0-False 1-True             |

## MainConfigObject

> Offset: ObjectReference.Offset

| Bytes               | Field                      | Type   | Description                                   |
| ------------------- | :------------------------- | :----- | --------------------------------------------- |
| 4                   | Unknown                    | UInt32 | CRC or Record Type                            |
| 4                   | HeaderSize                 | UInt32 |                                               |
| 4                   | Unknown                    | UInt32 | Device Related                                |
| 4                   | Unknown                    | UInt32 | Device Related                                |
| 4                   | DeviceId                   | UInt32 | See Lookup                                    |
| 4                   | Unknown                    | UInt32 | Device Related                                |
| 4                   | ContentOffset              | UInt32 |                                               |
| 4                   | ContentCount               | UInt32 |                                               |
| 4                   | Unknown                    | UInt32 |                                               |
| 4                   | ContentTypeCount           | UInt32 | Number of Object Types represented (i, is, p) |
| 16 * `ContentCount` | ContentEntry(ContentCount) | Array  |                                               |

## ContentEntry

> Offset: FileObjectEntry.ObjectOffset+ContentOffset

| Bytes | Field | Type   | Description |
| ----- | :---- | :----- | :---------- |
| 8     | Type  | String |             |
| 8     | Name  | String |             |

## ProgramObject

> Offset: FileObjectEntry.ObjectOffset
 
| Bytes                        | Field    | Type   | Description |
| :--------------------------- | :------- | :----- | :---------- |
| `FileObjectEntry.ObjectSize` | ProgramS | String |             |

## ImageObject

> Offset: FileObjectEntry.ObjectOffset

| Bytes       | Field       | Type   | Description               |
| ----------- | :---------- | ------ | ------------------------- |
| 4           | Unknown     | UInt32 | Crc or RecType            |
| 4           | Unknown     | UInt32 |                           |
| 4           | Unknown     | UInt32 |                           |
| 4           | HeaderSize  | UInt32 |                           |
| 2           | ImageWidth  | UInt16 |                           |
| 2           | ImageHeight | UInt16 |                           |
| 4           | ImageSize   | UInt32 |                           |
| 4           | Unknown     | UInt32 | High Bytes of ImageSize   |
| `ImageSize` | Image       | Byte() | RGB565 Bitmap /wo Headers |

> Image - RGB565 image /wo standard BMP header. See RGB565 Encoding/Decoding for more information 

## ImageSourceObject

> Offset: FileObjectEntry.ObjectOffset

| Bytes       | Field       | Type          | Description             |
| ----------- | :---------- | ------------- | ----------------------- |
| 4           | Unknown     | UInt32        | Crc or RecType          |
| 4           | Unknown     | UInt32        |                         |
| 4           | Unknown     | UInt32        |                         |
| 2           | ImageWidth  | UInt16        |                         |
| 2           | ImageHeight | UInt16        |                         |
| 4           | ImageSize   | UInt32        |                         |
| 4           | Unknown     | UInt32        | High Bytes of ImageSize |
| 3           | ImageType   | String(fixed) |                         |
| `ImageSize` | Image       | Byte()        | Original Image          |

> Image - Original image stored directly inside

## FontObject

> Offset: FileObjectEntry.ObjectOffset

| Bytes | Field | Type | Description |
| ----- | - | - | - | 


## PageObject

> Offset: FileObjectEntry.ObjectOffset

| Bytes | Field                     | Type   | Description    |
| ----- | ------------------------- | :----- | -------------- |
| 4     | Unknown                   | UInt32 | Crc or RecType |
| 4     | Size                      | UInt32 |                |
| 4     | HeaderSize                | UInt32 |                |
| 4     | ComponentCount            | UInt32 |                |
| 4     | Unknown                   | UInt32 |                |
| 4     | Unknown                   | UInt32 |                |
| 16    | Name                      | String |                |
| 4     | Unknown                   | UInt32 |                |
| 4     | Unknown                   | UInt32 |                |
| 4     | Unknown                   | UInt32 |                |
| 4     | Unknown                   | UInt32 |                |
|       | Component(ComponentCount) | Array  |                |

## Component

| Bytes | Field                       | Type          | Description |
| :---- | :-------------------------- | :------------ | :---------- |
| 4     | AttributesOffset            | UInt32        |             |
| 4     | AttributesSize              | UInt32        |             |
| 4     | Unknown                     | UInt32        |             |
| 4     | AttrCntSize                 | UInt32        |             |
| 4     | AttrTag                     | String(Fixed) |             |
| 12    | AttrCnt                     | String        |             |
|       | Attribute(Value(AttrCnt)-1) | Array         |             |

## Attribute

| Bytes     | Field | Type   | Description  |
| :-------- | :---- | :----- | :----------- |
| 4         | Size  | UInt32 |              |
| 16        | Name  | String |              |
| `Size`-16 | Value | UInt   | (IF Size>16) |