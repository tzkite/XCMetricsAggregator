![](./assets/XCMetricsAggregator.png)

## What's this?

XCMetricsAggregator aggregates metrics across all apps from [Xcode Metrics Organizer](https://help.apple.com/xcode/mac/current/#/devb642b28ac) by automating Xcode with AppleScript.

## Setup

1. Install Xcode from App Store

2. Add your Apple ID to Accounts preferences in Xcode

3. Download this script
```
git clone https://github.com/yahoojapan/XCMetricsAggregator.git
```

## Run

Run `run.sh` from the Terminal.
```
./run.sh
```

## Run with Launchd

If you would like to run script periodically, you can use launchd.

Create plist file to `~/Library/LaunchAgents/xcode-metrics.plist`. 

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>xcode-metrics</string>
    <key>ProgramArguments</key>
    <array>
        <string>/bin/sh</string>
        <string>/your/path/xcode-metrics-automation/run.sh</string>
    </array>
    <key>StartCalendarInterval</key>
    <dict>
      <key>Hour</key>
      <integer>12</integer>
      <key>Minute</key>
      <integer>10</integer>
    </dict>
    <key>StandardOutPath</key>
    <string>/tmp/xcode-metrics.out</string>
    <key>StandardErrorPath</key>
    <string>/tmp/xcode-metrics.err</string>
</dict>
</plist>
```

Run this command in Terminal to enable the setting.

```
launchctl load ~/Library/LaunchAgents/xcode-metrics.plist
```

## License

This software is released under the MIT License, see LICENSE.
