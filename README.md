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
* [HERO 10](/hero10)

[All files contain GPMF/GPMD telemetry](https://github.com/gopro/gpmf-parser).

## Download files used to generate metadata

* Library of files: https://docs.google.com/spreadsheets/d/1iEoSwvziu27XJ8TEsvXcERy6DpHtdO0NtxpO1zzpqlw/edit?usp=sharing
* Actual metadata output: https://drive.google.com/drive/folders/196l5H__7vh_UhuE7EF9qFy4t6GJVasYU?usp=drive_link

## Relevant Posts for understanding GPMF

A lot of the content from the posts below has been summarised in the [Notes](/notes/) section of this repository.

For reference;

* [GoPro explain GPMF](https://gopro.com/en/us/news/gopro-video-metadata-open-source-explained).
* [A GPMF-parser was recently made available as an open source project](https://github.com/gopro/gpmf-parser)
* [Also a GPMF writer from GoPro](https://github.com/gopro/gpmf-write)
* [Some useful GPMF focused scripts](https://github.com/stilldavid/gopro-utils)
* [GMPF format is also understood by the open-source Exiftool](https://exiftool.org/). [The logic used in exiftool for extraction can be viewed here](https://github.com/exiftool/exiftool/blob/master/lib/Image/ExifTool/GoPro.pm).
* [An Introduction to the GoPro Metadata Format (GPMF) standard (video telemetry)](https://www.trekview.org/blog/2020/metadata-exif-xmp-360-video-files-gopro-gpmd)
* [An Introduction to the Camera Motion Metadata (CAMM) standard (video telemetry)](https://www.trekview.org/blog/2021/metadata-exif-xmp-360-video-files-camm-camera-motion-metadata-spec/)
* [GPMF Metadata Notes](https://guides.trekview.org/explorer/developer-docs/sequences/process/gopro-video-telemetry).
* [What are XMP Namespaces?](https://www.trekview.org/blog/2021/introduction-to-xmp-namespaces/)
* [A deeper look into a 360 photo and the metadata it holds](https://www.trekview.org/blog/2020/metadata-exif-xmp-360-photo-files/)
* [A deeper look at 360 video projections](https://www.trekview.org/blog/2021/projection-type-360-photography/)

## License

* Code: [Apache 2.0](/LICENSE).
* Images: [CC BY-SA 4.0](/LICENSE-IMAGES).