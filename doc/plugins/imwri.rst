.. _imwri:

ImageMagick Writer-Reader
=========================

ImageMagick Writer-Reader (IMWRI) is a plugin that can read and write many image formats with up to 16 bits per channel.

.. function:: Write(clip clip, string imgformat, string filename[, int firstnum = 0, int quality=75, bint dither=1, clip alpha])
   :module: imwri

   Write will write each frame to disk as it's requested. If a frame is never requested it's also never written to disk.
 
   Parameters:
      clip
         Input clip. Only 8-16 bit RGB supported. Variable dimensions are allowed.

      imgformat
         The name of the output format. Examples of supported format strings are JPEG, PNG and DPX. Visit the ImageMagick website for a full list.
         
      filename
         The filename string must have one or more frame number substitutions. The syntax is printf style. For example "image%06d.png" or "/images/%d.jpg" is common usage.

      firstnum
         The first image number in the sequence to write.
         
      quality
         Quality adjustment for formats where it's applicable. Range is 0 to 100.

      dither
         Use Floyd–Steinberg if the input needs to be reduced in depth.

      alpha
         A grayscale clip containing the alpha channel for the image to write. Apart from being grayscale its properties must be identical to the main *clip*.



.. function:: Read(string[] filename[, int firstnum = 0, bint mismatch=0, bint alpha=0])
   :module: imwri

   Read is a simple function for reading single or series of images and returning them as a clip.

   Parameters:
      filename
         The filename has argument has two main modes. Either it takes a list of 1 or more files to open in the given order or it takes a single filename string with one or more frame number substitutions. The syntax is printf style. For example "image%06d.png" or "/images/%d.jpg" is common usage.

      firstnum
         The first image number to start reading from when reading a sequence.
         
      mismatch
         Allow reading of multiple images with different resolution, if not set an error will be generated.

      alpha
         Return the alpha channel from the read images as a separate grayscale clip. Note that an alpha channel clip is always returned when set, even for image formats without support for it.