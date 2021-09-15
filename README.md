# GoPro Metadata

## In one sentence

This repository exists to accumulate and understand the metadata produced by GoPro  cameras.

## Why we built this

We build software that processes GoPro video and image files. In many cases these files contain telemetry data (e.g are geotagged).

Before processing them, we need to understand the format (or standard) of files each camera produces to process it correctly.

## Cameras tested

* [Fusion](/fusion)
* [MAX](/max)

## GPMF 101

All GoPro cameras write video telemetry data (GPS) in their own GoPro Metadata Format (GPMF / GPMD) also called the General Purpose Metadata Framework.

[This blog post provides a good introduction](https://gopro.com/en/us/news/gopro-video-metadata-open-source-explained).

[A GPMF-parser was recently made available as an open source project](https://github.com/gopro/gpmf-parser). This repo explains the standard in detail.

[The format is also understood by the open-source Exiftool](https://exiftool.org/). [The logic used in exiftool for extraction can be viewed here](https://github.com/exiftool/exiftool/blob/master/lib/Image/ExifTool/GoPro.pm).

Other useful tools for understanding / using GPMF:

* https://github.com/stilldavid/gopro-utils
* https://github.com/gopro/gpmf-write

## .LRV / .THM

When shooting GoPro videos, the camera will also create .LRV and .THM files.

LRV files are low-resolution video files used by GoPros as video previews. THM files are JPG thumbnails used by GoPros as photo previews. Both are used by the GoPro mobile apps. You can safely delete both filetypes — they'll be regenerated from the original MP4 or image file if needed.

## License

All sample files used to extract metadata are offered free of charge for the benefit of other developers under and MIT license / CC BY 4.0 license.