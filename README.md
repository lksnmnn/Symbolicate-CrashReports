# Symbolicate Crash Reports
This script is based on Apple's symbolicate script. It now symbolicates Mac and iOS crash reports from PLCrashReporter.

Written in Perl.

## Usage

Currently, the script has to be placed in the following directory:
```/Applications/Xcode.app/Contents/SharedFrameworks/DTDeviceKitBase.framework/Versions/A/Resources/s```

Make sure you have your *YOUR_APP.dSYM* and *YOUR_APP.app* files on your machine. The script should find them. The following will symbolicate your crash report and save it to *readable_report.crash*

```
# set the developer directory
export DEVELOPER_DIR="/Applications/Xcode.app/Contents/Developer"

# Now run the script
/Path/To/symbolicatecrash /Path/To/report.crash > /Path/To/readable_report.crash
```

Use -v for verbose logging.

For proper reports and symbols, set your build settings to this:
```
Strip Debug Symbols During Copy: Yes
Strip Style: All Symbols
Strip Linked Product: Yes
```

## Changes

At first I fixed the search paths for the used tools (like otool, atos, ...), added x86_64 as a viable architecture and implemented a minor fix to extract the executable from the .app bundle.

If found this article particular useful: [https://possiblemobile.com/2015/03/symbolicating-your-ios-crash-reports/](https://possiblemobile.com/2015/03/symbolicating-your-ios-crash-reports/)

## Known Bugs

The script only works within its previous location (the XCode package). If the report is malformed (like iOS crash reports from PLCrahsReporter) it could hang. One needs to remove duplicated binaries in the original report. 

## Credits

You will find the original script here: 
```
/Applications/Xcode.app/Contents/SharedFrameworks/DTDeviceKitBase.framework/Versions/A/Resources/symbolicatecrash
```

Edited by lksnmnn

Copyright (c) 2008-2011 Apple Inc. All Rights Reserved.
