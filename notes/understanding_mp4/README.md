# 0. Introduction

MPEG-4 is a group of international standards for the compression of digital audio and visual data, multimedia systems, and file storage formats. It was originally introduced in late 1998 as a group of audio and video coding formats and related technology agreed upon by the ISO/IEC Moving Picture Experts Group under the formal standard ISO/IEC 14496 - Coding of audio-visual objects.

The basic data unit in this file is the atom. Each atom contains size and type fields that precede any other data. The size field indicates the total number of bytes in the atom, including the size and type fields. The type field specifies the type of data stored in the atom and, by implication, the format of that data. In some cases, the size and type fields are followed by a version field and a flags field. An atom with these version and flags fields is sometimes called a full atom.

# 1. Mdat

In simpler terms `mdat` contains all the main data of the video and can be accessed using `moov` atom.

# 2. Moov

These atoms act as a container for the information that describes a movie's data. This information, or metadata, is stored in a number of different types of atoms. Generally speaking, only metadata is stored in a movie atom. Sample data for the movie, such as audio or video samples, are referenced in the movie atom, but are not contained in it.

The movie atom is essentially a container of other atoms. These atoms, taken together, describe the contents of a movie. At the highest level, movie atoms typically contain track atoms, which in turn contain media atoms. At the lowest level are the leaf atoms, which contain non-atom data, usually in the form of a table or a set of data elements. For example, a track atom contains an edit atom, which in turn contains an edit list atom, a leaf atom which contains data in the form of an edit list table. All of these atoms are discussed later in this document.

# 2.1. Mvhd

From mvhd we can get information about the video for eg.

- creation time (4)
- modification time (4)
- timescale (4)
- duration (4)
- preferred_rate (4)
- preferred_volume (2)
- reserved (10)
- matrix_structure (36)
- preview_time (4)
- preview_duration (4)
- poster_time (4)
- selection_time (4)
- selection_duration (4)
- current_time (4)
- next_track_id (4)

# 2.2. Trak

Trak Atom
- Atom Size
- Type = 'trak'
    - tkhd
    - mdia
    - edts
    - tref
    - udta

# 2.2.1. Tkhd

Tkhd Atom
- Atom Size
- Type = 'tkhd'
    - version (1)
    - flags (3)
    - creation time (4)
    - modification time (4)
    - track id (4)
    - reserved (4)
    - duration (4)
    - reserved (8)
    - layer (2)
    - alternate group (2)
    - volume (2)
    - reserved (2)
    - matrix structure (36)
    - track width (4)
    - track height (4)

# 2.2.2. Mdia

Mdia Atom
- Atom Size
- Type = 'mdia'
    - mdhd
    - elng
    - hdlr
    - minf
    - udta

# 2.2.2.1 Mdhd

Mdhd Atom
- Atom Size
- Type = 'mdhd'
    - version (1)
    - flags (3)
    - creation time (4)
    - modification time (4)
    - time scale (4)
    - duration (4)
    - language (2)
    - quality (2)

# 2.2.2.2 Hdlr

Hdlr Atom
- Atom Size
- Type = 'hdlr'
    - version (1)
    - flags (3)
    - component type (4)
    - component sub type (4)
    - component manufacturer (4)
    - component flags (4)
    - component flags mask (4)
    - component name (4)

# 2.2.2.3 Minf

Minf Atom
- Atom Size
- Type = 'minf'
    - hdlr
    - stbl

# 2.2.2.3.1 Stbl

Stbl Atom
- Atom Size
- Type = 'stbl'
    - stsd
    - stts
    - stco
    - co64
    - stsc
    - stsz

# 2.2.2.3.1.1 Stsd

Stsd Atom
- Atom Size
- Type = 'stsd'
    - version (1)
    - flags (3)
    - Number of entries (4)
    - Sample Description Table
        - Data Format (4)
        - Reserved (0)
        - Data Refrence Index (2)

# 2.2.2.3.1.1.1 Camm
    Camera Motion Metadata
# 2.2.2.3.1.1 Stts

Stts Atom
- Atom Size
- Type = 'stts'
    - version (1)
    - flags (3)
    - Number of entries (4)
    - Time To Sample Table
        - Sample Count (4)
        - Sample Duration (4)

# 2.2.2.3.1.1 Stsc

Stsc Atom
- Atom Size
- Type = 'stsc'
    - version (1)
    - flags (3)
    - Number of entries (4)
    - Sample To Chunk Table 
        - First Chunk
        - Samples Per Chunk
        - Sample Description Id

# 2.2.2.3.1.1 Stsz

Stsz Atom
- Atom Size
- Type = 'stsz'
    - version (1)
    - flags (3)
    - Sample Size (4)
    - Number of entries (4)
    - Sample Size Table
        - Samples

# 2.2.2.3.1.1 Co64

Co64 Atom
- Atom Size
- Type = 'co64'
    - version (1)
    - flags (3)
    - Number of entries (4)
    - Chunk Offset Table
        - Chunks 

# 2.2. Udta

User Data Atom
- Atom Size
- Type = 'udta'
    User Data List
    - Atom Size
    - Type = user data types
        User Data List

## 2.2.1. Spherical Metadata

We can also see `udta` container holds the `make`, `model` and additional `metadata` about the image.

In video track `uuid` we can find spherical metadata which looks like below:

<rdf:SphericalVideo xmlns:GSpherical='http://ns.google.com/videos/1.0/spherical/'
xmlns:rdf='http://www.w3.org/1999/02/22-rdf-syntax-ns#'>
    <GSpherical:Spherical>true</GSpherical:Spherical>
    <GSpherical:Stitched>true</GSpherical:Stitched>
    <GSpherical:ProjectionType>equirectangular</GSpherical:ProjectionType>
    <GSpherical:StereoMode>mono</GSpherical:StereoMode>
    <GSpherical:StitchingSoftware>Insta360</GSpherical:StitchingSoftware>
    <GSpherical:SourceCount>2</GSpherical:SourceCount>
</rdf:SphericalVideo>