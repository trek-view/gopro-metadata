# GoPro MAX Overview

* Manufacturer: GoPro
* Model: MAX
* On Sale: 2019 - Present
* [User Manual](/MAX_UM_ENG_REVA.pdf)

## Modes 

### 360 Modes

* Unprocessed Video
	* 360 Video (output .`360`)
		* [5.6K stitched (24FPS)](#56k-stitched--24fps-output-360)
		* [5.6K stitched (30FPS)](#56k-stitched--30fps-output-360)
		* [3k stitched (60 FPS)](#3k-stitched--60fps-output-360)
	* 360 TimeWarp stitched (output `.360`)
		* 5x rate
* Processed Video (output of GoPro Studio)
	* 360 Video (output `.mp4`)
		* 5.6K blended (24FPS, 30FPS)
		* 3k blended (60 FPS)
	* 360 TimeWarp blended (output `.mp4`)
		* (2x,5x,10x,15x,30x frame rate)
	* HERO Video (output `.mp4`)
		* 1440 @60 FPS
		* 1080 @60 FPS
		* 1080 @60 FPS Max SuperView
	* HERO Timewarp 1080 Auto
		* (Auto frame rate)
* Timelapse photo
	* 360 TimeLapse 360 (output `.jpg`)
		* 16.6MP stitched (2s, 5s, 10s, 30s, 60s interval)
	* HERO Photo (output `.jpg`)
		* 1080 output (wide)

### Notes

#### .360's

All videos shot on the MAX are stitched as `.360` files on the camera. This is a propriatory GoPro format (with EAC projection). [Using GoPro Player](https://community.gopro.com/t5/en/GoPro-Player/ta-p/413305) you can convert to mp4 (with equirectanguar projection).

#### Download Samples

[Download the all the samples here](https://drive.google.com/drive/folders/1T2-ntDGtvBJlgDOmNwrKAQfvkP8leIQD?usp=sharing).

[All files in this analysis contain GPMF/GPMD telemetry](https://github.com/gopro/gpmf-parser).

## Metadata Samples

### Unprocessed Videos

The GoPro MAX writes `.360` files to the SD card. `.360` is a GoPro proprietary format. .360's use EAC projections.

Video file names are preface with `GS` and increase sequentially numerically based on existing files on memory card (e.g. `GS018423.360`, `GS018424.360`.

When shooting video longer than 8 mins (about 4GB), GoPro creates a new .360 file (put another way; .360 video files are chunked into 8min/4gb outputs).

#### 360 Video

##### 5.6K stitched @ 24FPS (output `.360`)

###### Input:

```
exiftool -ee -G3 -api LargeFileSupport=1 -X GS018422.360 > GS018422.xml
```

###### Output:

[GS018422.xml](/max/GS018422.xml)

##### 5.6K stitched @ 30FPS (output `.360`)

###### Input:

```
exiftool -ee -G3 -api LargeFileSupport=1 -X GS018421.360 > GS018421.xml
```

###### Output:

[GS018421.xml](/max/GS018421.xml)

##### 3K stitched @ 60FPS (output `.360`)

###### Input:

```
exiftool -ee -G3 -api LargeFileSupport=1 -X GS018423.360 > GS018423.xml
```

###### Output:

[GS018423.xml](/max/GS018423.xml)

##### TimeWarp @ 5.6k 5x (output `.360`)

###### Input:

```
exiftool -ee -G3 -api LargeFileSupport=1 -X GS018424.360 > GS018424.xml
```

###### Output:

[GS018424.xml](/GS018424.xml)

### Processed Videos

#### 360 Video

Users can convert `.360`'s into a more available standard using [GoPro Studio](https://community.gopro.com/t5/en/GoPro-Player/ta-p/413305). This software allows for some video adjustments (e.g. horizon leveling) during processing. Outputted mp4's use equirectangular projections.

Note: the GPMF metadata (telemetry) is not retained on the Windows version of GoPro Studio.

The files used here were stitched on a Mac in h264 with no additional setting enabled (e.g. Horizon levelling).

##### 5.6K stitched @ 24FPS (output `.mp4`)

###### Input:

```
exiftool -ee -G3 -api LargeFileSupport=1 -X GS018422.mp4 > GS018422_mp4.xml
```

###### Output:

[GS018422_mp4.xml](/max/GS018422_mp4.xml)

##### 5.6K stitched @ 30FPS (output `.mp4`)

###### Input:

```
exiftool -ee -G3 -api LargeFileSupport=1 -X GS018421.mp4 > GS018421_mp4.xml
```

###### Output:

[GS018421_mp4.xml](/max/GS018421_mp4.xml)

##### 3K stitched @ 60FPS (output `.mp4`)

###### Input:

```
exiftool -ee -G3 -api LargeFileSupport=1 -X GS018423.mp4 > GS018423_mp4.xml
```

###### Output:

[GS018423_mp4.xml](/max/GS018423_mp4.xml)

#### 360 Timewarp

##### TimeWarp @ 5.6k (output `.mp4`)

###### Input:

```
exiftool -ee -G3 -api LargeFileSupport=1 -X GS018424.mp4 > GS018424_mp4.xml
```

###### Output:

[GS018424_mp4.xml](/max/GS018424_mp4.xml)

#### HERO Video

##### 1440 @60 FPS (output .`mp4`)

###### Input:

```
exiftool -ee -G3 -api LargeFileSupport=1 -X GH018429.MP4 > GH018429_mp4.xml
```

###### Output:

[GH018429_mp4.xml](/max/GH018429_mp4.xml)

##### 1080 @60 FPS (output .`mp4`)

###### Input:

```
exiftool -ee -G3 -api LargeFileSupport=1 -X GH018427.MP4 > GH018427_mp4.xml
```

###### Output:

[GH018429_mp4.xml](/max/GH018427_mp4.xml)

##### 1080 @60 FPS Max SuperView (output .`mp4`)

###### Input:

```
exiftool -ee -G3 -api LargeFileSupport=1 -X GH018428.MP4 > GH018428_mp4.xml
```

###### Output:

[GH018429_mp4.xml](/max/GH018429_mp4.xml)

#### HERO Timewarp

Timewarps can be set at a number of framerates from 2x to 60x (or auto, where GoPro decides best rate)

##### Timewarp 1080 Auto (output .`mp4`)

###### Input:

```
exiftool -ee -G3 -api LargeFileSupport=1 -X GH018426.MP4 > GH018426_mp4.xml
```

###### Output:

[GH018429_mp4.xml](/max/GH018426_mp4.xml)

---

### Timelapse photo (.jpg)

#### 360 Timelapse

Spherical .jpgs are stitched on camera.

Timelapse file names are preface with `GS` . Each unique timelapse is prefaced with two characters starting at AA, and increase sequentially alphabetically based on existing timelapses on memory card (e.g. `GSAA`, `GSAB`. Each photo in timelapse is assigned a number starting at 0001. The next timelapse photo follows the same sequential numerical order (e.g. GSAA0001.jpg - GSAA0991.jpg, GSAB0992.jpg - GSAB2001.jpg).

##### 16.6mp output (output `.jpg`)

###### Input:

```
exiftool -X GSAD3685.JPG > GSAD3685.xml
```

###### Output:

[GSAD3685.JPG](/max/GSAD3685.xml)

#### HERO Timelapse photo 

.jpgs are stitched on camera.

Timelapse file names are preface with `GP` . Each unique timelapse is prefaced with two characters starting at AA, and increase sequentially alphabetically based on existing timelapses on memory card (e.g. `GPAA`, `GPAB`. Each photo in timelapse is assigned a number starting at 0001. The next timelapse photo follows the same sequential numerical order (e.g. GPAA0001.jpg - GPAA0991.jpg, GPAB0992.jpg - GPAB2001.jpg).

##### 1080 output (wide) (output `.jpg`)

###### Input:

```
exiftool -X GPAA8441.JPG > GPAA8441.xml
```

###### Output:

[GSAD3685.JPG](/max/GPAA8441.xml)
