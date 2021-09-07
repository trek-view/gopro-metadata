# GoPro Fusion (Explorer)

## Explorer Checks

### For `.mp4`

###### Is GoPro Fusion:

```
<Track3:DeviceName>Fusion</Track3:DeviceName>
```

###### Is stitched by GoPro Fusion Studio

```
<XMP-GSpherical:StitchingSoftware>Fusion Studio / GStreamer</XMP-GSpherical:StitchingSoftware>
```

###### Is equirectangular 

```
<XMP-GSpherical:ProjectionType>equirectangular</XMP-GSpherical:ProjectionType>
```

###### Has GoPro telemetry:

```
<Track3:MetaFormat>gpmd</Track3:MetaFormat>
```

###### Is correct frame rate

**60 FPS (3k)**

NEED SAMPLE

**30 FPS (5.6k)**

```
<Track1:VideoFrameRate>29.97</Track1:VideoFrameRate>
```

###### Is correct resolution:

**3k (60 FPS)**

NEED SAMPLE

**5.6k (24 FPS, 30 FPS)**

```
<Track1:ImageWidth>3840</Track1:ImageWidth>
 <Track1:ImageHeight>1920</Track1:ImageHeight>
```

###### Is longer than 10 seconds:

```
<Track1:TrackDuration>15.98 s</Track1:TrackDuration>
```

### For `.jpg`

###### Is GoPro Fusion:

```
<IFD0:Make>GoPro</IFD0:Make>
<IFD0:Model>GoPro Fusion FS1.04.01.80.00</IFD0:Model>
```

_Note: only GoPro Fusion needs to exist in IFD0:Model tag._

###### Is equirectangular:

```
<XMP-GPano:ProjectionType>equirectangular</XMP-GPano:ProjectionType>
```