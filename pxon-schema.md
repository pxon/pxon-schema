# PXON schema

## structure

PXON is <abbr title="JavaScript Object Notation">[JSON](http://json.org/)</abbr> representing pixel art.

There are two objects in PXON, <abbr title="Exchangeable image file format">[Exif](http://www.w3.org/2003/12/exif/)</abbr> and <abbr title="pixel image file format">`pxif`</abbr>. `exif` has any properties defined by the Exif <abbr title="Resource Description Framework">[RDF](http://www.w3.org/RDF/)</abbr> schema. For the sake of creating pixel art, many of these properties are not necessary or even applicable. They have been narrowed down to:


* `software`: (string) the software used to create/export the pxon
* `artist`: (string) the identity of the artist of the work the pxon represents
* `imageDescription`: (string) a description of the image
* `userComment`: (string) a comment from the user generating the pxon
* `copyright`: (string) the copyright of the image
* `dateTime`: (string) the date/Time the pxon was initially generated
* `imageWidth`: (integer) the display pixel width of the image canvas
* `imageLength`: (integer) the display pixel height of the image canvas


`pxif` is the pixel art spin of `exif`, in essense it is unique to pixel art and breaks down the image beyond it's typical metadata and focuses on the individual strokes and drawings of the pixels within the image. The first property, `pixels` is an array of "pixel" objects representing the pixels drawn in the image. Because it is a new idea in this format, the list of properties is fluid and ever changing at the moment. They are:


* `x` - (integer) the x coordinate position of the pixel
* `y` - (integer) the y coordinate position of the pixel
* `color` - (string) the color of the pixel
* `size` - (integer) the size in px of the pixel


A `dataURL` property has a string value of the dataURL of the canvas the pixel art had when pxon is exported. This may be helpful for drawing the inital image on pxon import but it may be best to just redraw each pixel in the `pixels` array. Until the apps using pxon are refined, it's best to keep this property here I believe.

```json
{
  "exif": {
    "software"          : "",
    "artist"            : "",
    "imageDescription"  : "",
    "userComment"       : "",
    "copyright"         : "",
    "dateTime"          : "",
    "imageWidth"        : 0,
    "imageLength"       : 0
  },
  "pxif": {
    "pixels"  : [
      {
        "x"  : 0,
        "y"  : 0,
        "color" : "",
        "size"  : 0
      }
    ],
    "dataURL" : ""
  }     
}
```
