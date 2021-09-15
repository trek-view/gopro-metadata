# GoPro MAX (Explorer)

## Explorer Checks

### For `.360`

###### Is GoPro MAX:

```
<GoPro:Model>GoPro Max</GoPro:Model>
```

###### Is .360 format (and shot in 360 mode)

```
<Track1:CompressorName>GoPro H.265 encoder</Track1:CompressorName>
```

###### Has GoPro telemetry:

**Normal Video**

```
<Track4:MetaFormat>gpmd</Track4:MetaFormat>
```

**Timewarp video**

```
<Track3:MetaFormat>gpmd</Track3:MetaFormat>
```

###### Is video or timewarp

**Normal Video**

```
<Track6:CompressorName>GoPro H.265 encoder</Track6:CompressorName>
```

**Timewarp video**

```
<Track5:CompressorName>GoPro H.265 encoder</Track5:CompressorName>
```

###### Is correct frame rate

**24 FPS (5.6k)**

```
<Track1:VideoFrameRate>23.976</Track1:VideoFrameRate>
```

**30 FPS (5.6k)**

```
<Track1:VideoFrameRate>29.97</Track1:VideoFrameRate>
```

**60 FPS (3k)**

```
<Track1:VideoFrameRate>59.94</Track1:VideoFrameRate>
```

###### Is correct resolution:

**3k (60 FPS)**

```
<Track1:ImageWidth>2272</Track1:ImageWidth>
<Track1:ImageHeight>736</Track1:ImageHeight>
```

**5.6k (24 FPS, 30 FPS)**

```
<Track1:ImageWidth>4096</Track1:ImageWidth>
<Track1:ImageHeight>1344</Track1:ImageHeight>
```

###### Is longer than 10 seconds:

```
<Track1:TrackDuration>20.22 s</Track1:TrackDuration>
```

###### If timewarp what rate setting used

```
<GoPro:Rate>5X</GoPro:Rate>
```

---

### For `.mp4`

###### Is GoPro MAX:


**Normal Video**

```
<Track3:DeviceName>GoPro Max</Track3:DeviceName>
```

**Timewarp video**

```
<Track2:DeviceName>GoPro Max</Track2:DeviceName>

```

###### Is stitched by GoPro Studio

```
<XMP-GSpherical:StitchingSoftware>Spherical Metadata Tool</XMP-GSpherical:StitchingSoftware>
```

###### Is equirectangular 

```
<XMP-GSpherical:ProjectionType>equirectangular</XMP-GSpherical:ProjectionType>
```

###### Has GoPro telemetry:

**Normal Video**

```
<Track3:MetaFormat>gpmd</Track3:MetaFormat>
```

**Timewarp video**

```
<Track2:MetaFormat>gpmd</Track2:MetaFormat>
```

###### Is correct framerate

**24 FPS (5.6k)**

```
<Track1:VideoFrameRate>23.976</Track1:VideoFrameRate>
```

**30 FPS (5.6k)**

```
<Track1:VideoFrameRate>29.967</Track1:VideoFrameRate>
```

**60 FPS (3k)**

```
<Track1:VideoFrameRate>59.941</Track1:VideoFrameRate>
```

###### Is correct resolution:

**3k (60 FPS)**

```
<Track1:ImageWidth>3072</Track1:ImageWidth>
<Track1:ImageHeight>1536</Track1:ImageHeight>
```

**5.6k (24 FPS, 30 FPS)**

```
<Track1:ImageWidth>5376</Track1:ImageWidth>
<Track1:ImageHeight>2688</Track1:ImageHeight>
```

###### Is longer than 10 seconds:

```
<Track1:TrackDuration>15.98 s</Track1:TrackDuration>
```

###### If timewarp

**Normal Video**

```
<Track3:MetaFormat>gpmd</Track3:MetaFormat>
```

**Timewarp video**

```
<Track2:MetaFormat>gpmd</Track2:MetaFormat>
```

---

### For `.jpg`

###### Is GoPro MAX:

```
<IFD0:Model>GoPro Max</IFD0:Model>
```

###### Is equirectangular:

```
<XMP-GPano:ProjectionType>equirectangular</XMP-GPano:ProjectionType>
```