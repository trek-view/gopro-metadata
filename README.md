# GoPro 360 Metadata

## In one sentence

This repository exists to accumulate and understand the metadata produced by GoPro 360 cameras.

## Why we built this

We build software that processes 360 video and image files. In many cases these files contain telemetry data (e.g are geotagged).

Before processing them, we need to understand the format (or standard) of files each camera produces to process it correctly.

## Cameras

* [Fusion](/fusion)
* [MAX](/max)

## GPMF 101

All GoPro 360 cameras write data in their own GoPro Metadata Format (GPMF / GPMD) also called the General Purpose Metadata Framework.

[This blog post provides a good introduction](https://gopro.com/en/us/news/gopro-video-metadata-open-source-explained).

[A GPMF-parser was recently made available as an open source project](https://github.com/gopro/gpmf-parser). This repo explains the standard in detail.

[The format is also understood by the open-source Exiftool](https://exiftool.org/). [The logic used in exiftool for extraction can be viewed here](https://github.com/exiftool/exiftool/blob/master/lib/Image/ExifTool/GoPro.pm).

Other useful tools for understanding / using GPMF:

* https://github.com/stilldavid/gopro-utils
* https://github.com/gopro/gpmf-write

## License

All sample files used to extract metadata are offered free of charge for the benefit of other developers under and MIT license / CC BY 4.0 license.