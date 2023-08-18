# GoPro Metadata

## In one sentence

This repository exists to accumulate and understand the metadata produced by GoPro cameras.

## Why we built this

We build software that processes GoPro video and image files. In many cases these files contain telemetry data (e.g are geotagged).

Before processing them, we need to understand the format (or standard) of files each camera produces to process it correctly.

## Extraction logic

We use exiftool to extract metadata from both video and photo files like so:

```
exiftool -ee -G3 -api LargeFileSupport=1 -X INPUT.FILE > OUTPUT.xml
```

## Cameras currently covered

* [Fusion](/fusion)
* [MAX](/max)

[All files contain GPMF/GPMD telemetry](https://github.com/gopro/gpmf-parser).

## GPMF 101

All GoPro cameras write video telemetry data (GPS) in their own GoPro Metadata Format (GPMF / GPMD) also called the General Purpose Metadata Framework.

[This blog post provides a good introduction](https://gopro.com/en/us/news/gopro-video-metadata-open-source-explained).

[A GPMF-parser was recently made available as an open source project](https://github.com/gopro/gpmf-parser). This repo explains the standard in detail.

[The format is also understood by the open-source Exiftool](https://exiftool.org/). [The logic used in exiftool for extraction can be viewed here](https://github.com/exiftool/exiftool/blob/master/lib/Image/ExifTool/GoPro.pm).

Other useful tools for understanding / using GPMF:

* https://github.com/stilldavid/gopro-utils
* https://github.com/gopro/gpmf-write

## Relevant Trek View Blog Post / Documents


* [An Introduction to the GoPro Metadata Format (GPMF) standard (video telemetry)](https://www.trekview.org//blog/2020/metadata-exif-xmp-360-video-files-gopro-gpmd)
* [An Introduction to the Camera Motion Metadata (CAMM) standard (video telemetry)](https://www.trekview.org//blog/2021/metadata-exif-xmp-360-video-files-camm-camera-motion-metadata-spec/)
* [GPMF Metadata Notes](https://guides.trekview.org/explorer/developer-docs/sequences/process/gopro-video-telemetry).
* [What are XMP Namespaces?](https://www.trekview.org/blog/2021/introduction-to-xmp-namespaces/)
* [A deeper look into a 360 photo and the metadata it holds](https://www.trekview.org/blog/2020/metadata-exif-xmp-360-photo-files/)
* [A deeper look at 360 video projections
](https://www.trekview.org/blog/2021/projection-type-360-photography/)

## License

* Code: [Apache 2.0](/LICENSE).
* Images: [CC BY-SA 4.0](/LICENSE-IMAGES).