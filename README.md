# Annotations of form images from the National Archive

The goal of this data is to capture relationships between text/handwriting entities on form images. 
It will include transcriptions in the future, but doesn't currently.

The form images are organized into "groups", each group containing images of the same form type. 
I tried to be picky in keeping form seperate that contain even one different field, but it really is an estimate that was intented to speed up annotation.

The `groups` directory contains a directory for each group. 
Within each group directory there are jpg and json files, which are linked by having the same file name (except for extension).

The jsons have the following information:

* imageFilename: the image name this json corresponds to
* width & height: size of the original image (here for convienence)
* fieldBBs & textBBs: list of field/text bounding box objects
  * These objects have: 
    * poly_points: list of [x,y] pairs, the box corners going top-left,top-right,bottom-right,bottom-left
    * type: one of [text,textP,textMinor,textInst,textNumber,fieldCircle,field,fieldP,fieldCheckBox,graphic,comment,fieldRegion,fieldCol,fieldRow]
    * id: unique id that is either "f#" or "t#" depending if it is a field or text
    * isBlank: only for fields, has a number. 
      * 0: text
      * 1: handwriting
      * 2: print (or stamp)
      * 3: blank
      * 4: signature
* pairs: list of id tuples of relationships between text and field boxes
* samePairs: list of id tuples of relationships between text and text or field and field
* actualPage_corners: cordinates of phyisical page corners
* page_corners: cordinates of corners if the page where actually a polygon (e.g. not ripped corners)
* labelTime: sum of time spent labeling this image
* groups: deprecated
* horzLinks: list of "horizontal lines", each horizontal line being a list of ids of boxes that all form a horizontal line not broken by dividing lines or gaps.
* checkedBy: who checked the image
