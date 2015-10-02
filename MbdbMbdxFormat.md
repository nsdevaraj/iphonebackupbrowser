# Introduction #

iTunes 9.2 has changed Manifest.plist content and removed the .mdinfo files (and dropped the extension of .mddata files, however the 40 digit key is the same).

The files database is now stored in a couple of file: Manifest.mbdb and Manifest.mbdx. The applications list remains in Manifest.plist, but the format has (a little) changed.


# Details #

Important : all numbers are [big endian](http://en.wikipedia.org/wiki/Endianness).

## MBDX ##

(removed in iTunes 10.5 backups)

This is the index file.

### header ###
```
  uint8[6]    'mbdx\2\0'
  uint32      record count in the file
```

### record (fixed size of 26 bytes) ###

```
  uint8[20]  the Key of the file, it's also the filename in the backup directory
             It's the same key as 9.1 backups.
  uint32     offset of file record in .mbdb file
             Offsets are counted from the 7th byte. So you have to add 6 to this number to get the absolute position in the file.
  uint16     file mode
                 Axxx  symbolic link
                 4xxx  directory
                 8xxx  regular file
             The meaning of xxx is unknown to me, it corresponds to the Mode field in the old backup data.
```


## MBDB ##

### header ###
```
  uint8[6]    'mbdb\5\0'
```

### record (variable size) ###

```
  string     Domain
  string     Path
  string     LinkTarget          absolute path
  string     DataHash            SHA.1 (some files only)
  string     unknown             always N/A
  uint16     Mode                same as mbdx.Mode
  uint32     unknown             always 0
  uint32     unknown             
  uint32     UserId
  uint32     GroupId             mostly 501 for apps
  uint32     Time1               relative to unix epoch (e.g time_t)
  uint32     Time2               Time1 or Time2 is the former ModificationTime
  uint32     Time3
  uint64     FileLength          always 0 for link or directory
  uint8      Flag                0 if special (link, directory), otherwise unknown
  uint8      PropertyCount       number of properties following
```

Property is a couple of strings:
```
  string      name
  string      value               can be a string or a binary content
```

A string is composed of a uint16 that contains the length in bytes or 0xFFFF (for null or N/A) then the characters, in UTF-8 with canonical decomposition (Unicode normalization form D).