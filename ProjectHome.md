# Browse the files of local iPhone/iPod backups. #

## Description ##

This program shows the content of your iDevice backup.

No special access to the device is required, just **non-encrypted** backups made by iTunes 9.1.1 or 9.2 - 10.1.2 (as I write this), of course.

Select an app to show its files, or double-click it to open the .ipa archive in the Explorer.

You can drag a file to an editor, an image viewer, etc. Or double-click to show it in the Explorer. The filename consists in 40 hex digits and is not renamed (so, the default program associations will not work).


### 2010/06/27: support added for new backup files database ###

Last release of iTunes introduced a couple of new files: Manifest.mbdb and Manifest.mbdx. These files replace the old Manifest.plist and the plethora of files .mdinfo.

It's quite fun to see Apple abandon their property lists and XML for something completely propriatary.

See the [wiki page](http://code.google.com/p/iphonebackupbrowser/wiki/MbdbMbdxFormat) for an explanation of the file formats.


### 2011/02/13: now fetchs some information from the .IPA archives ###

The directory of .ipa must be _<User's Music>_\iTunes\Mobile Applications (this is the standard place).


## Requirements ##
This project requires Microsoft Visual C++ 2010 Express and Visual C# 2010 Express (and certainly a recent version of Windows).

You have to install the following packages:

[Visual C++ 2010 Runtime](http://www.microsoft.com/downloads/en/details.aspx?FamilyID=a7b7a05e-6de6-4d3a-a423-37bf0912db84)

[Microsoft .NET Framework 4 (Web Installer)](http://www.microsoft.com/downloads/en/details.aspx?FamilyID=9CFB2D51-5FF4-4491-B0E5-B386F32C0992) or [Microsoft .NET Framework 4 (Standalone Installer - 48.1 MB)](http://www.microsoft.com/downloads/en/details.aspx?FamilyID=0A391ABD-25C1-4FC0-919F-B21F31AB88B7)

**WARNING** For XP users:
Please install [Microsoft Internationalized Domain Names (IDN) Mitigation APIs 1.1](http://www.microsoft.com/downloads/details.aspx?FamilyID=AD6158D7-DDBA-416A-9109-07607425A815&amp;displaylang=ja-nec&displaylang=en) since BPLIST.DLL may use `NormalizeString` and `IsNormalizedString` new APIs. Or upgrade to Windows 7.

## Example ##
![http://iphonebackupbrowser.googlecode.com/files/screenshot-iphonebackupbrowser.jpg](http://iphonebackupbrowser.googlecode.com/files/screenshot-iphonebackupbrowser.jpg)

