# OBS Virtual Camera for macOS

![Build](https://github.com/johnboiles/obs-mac-virtualcam/workflows/Build%20and%20(maybe)%20Release/badge.svg)

Creates a virtual webcam device from the output of [OBS Studio](https://obsproject.com/). Especially useful for streaming smooth, composited video into Zoom, Hangouts, Jitsi etc. Like [CatxFish/obs-virtual-cam](https://github.com/CatxFish/obs-virtual-cam) but for macOS.

![Mar-28-2020 01-55-07](https://user-images.githubusercontent.com/218876/77819715-279b8700-709a-11ea-8885-aa15051665ee.gif)

This code was spun out of [this OBS Project RFC](https://github.com/obsproject/rfcs/pull/15) which was itself spun out of [this issue](https://github.com/obsproject/obs-studio/issues/2568) from [@tobi](https://github.com/tobi). The goal is for this (or something with equivalent functionality) to eventually be merged into the core OBS codebase 🤞.

## Known Issues

* Zoom prior to version 5.1.1 disabled virtual cameras by default. Please update to the latest (5.2.1 at time of writing) to re-enable virtual camera. Start the virtual camera before starting the Zoom application.
* Slack, Webex, Skype and probably some other applications have disabled virtual cameras by default via [application restrictions](https://developer.apple.com/documentation/bundleresources/entitlements/com_apple_security_cs_disable-library-validation?language=objc). Check out [the wiki](https://github.com/johnboiles/obs-mac-virtualcam/wiki/Compatibility) to see if your app is supported. Please [edit the wiki](https://github.com/johnboiles/obs-mac-virtualcam/wiki/Compatibility/_edit) if you try other software that we should include in that list. In most cases you can work around these restrictions by [re-codesigning those applications](https://github.com/johnboiles/obs-mac-virtualcam/wiki/Compatibility#apps-dont-allow-dal-plugins).
* Photo Booth and FaceTime do not support virtual cameras as of macOS 10.14 Mojave since they disallow loading any plugin that's not provided by Apple. Photo Booth can simply be duplicated and renamed (e.g. `Photo Booth copy`) and it will work. There is no known workaroud for FaceTime.
* You _may_ need to restart your computer after installing new versions of this plugin (not sure why 🤷‍♂️).

See also the open [issues](https://github.com/johnboiles/obs-mac-virtualcam/issues) for other reported issues. In case you need help or think you found a bug, see [this](https://github.com/johnboiles/obs-mac-virtualcam#Discussion--Support).

## Installing

* Download and install the latest version of OBS from the [official website](https://obsproject.com).
* Download the latest `.pkg` installer on the [Releases page](https://github.com/johnboiles/obs-mac-virtualcam/releases)
* Run the `.pkg` installer (entering your password when required)
* If you're already running OBS, make sure to restart it.
* Restart any app that was running during the installation process that is supposed to pick up the camera.
* To start the virtual camera, go (in OBS) to `Tools`→`Start Virtual Camera`.

Your OBS video should now show up in the target app!

## Uninstalling

You can easily uninstall this plugin by deleting the OBS plugin (in `/Library/Application\ Support/obs-studio/plugins/`) and the DAL plugin (in `/Library/CoreMediaIO/Plug-Ins/DAL/`).

```bash
sudo rm -rf /Library/CoreMediaIO/Plug-Ins/DAL/obs-mac-virtualcam.plugin
sudo rm -rf /Library/Application\ Support/obs-studio/plugins/obs-mac-virtualcam
```

## Discussion / Support

The official place for discussion and chat related to this plugin is in the `#plugins-and-tools` channel in the [OBS Studio Discord](https://discord.gg/obsproject). For questions or troubleshooting, ping @gxalpha#3486 and attach the OBS log, screenshots, and/or crash logs (from Console.app).

## Reporting Issues / Bugs / Improvements

> 🚀 Wonder How to contribute? Have look at our [notes for contributors](https://github.com/johnboiles/obs-mac-virtualcam/wiki/Contributing). There are ways non-technical or minimally-technical folks can contribute too!

This plugin is still very much a work in progress. If you are having an issue there's a good chance someone has already run into the same thing. Please search through the [issues](https://github.com/johnboiles/obs-mac-virtualcam/issues) before reporting a new one.

Also, make sure you're running the most recent version of OBS. We're only officially supporting the most recent version of OBS at any given time.

If you still believe you have found an unreported issue related to this plugin, please open an issue! When you do, include any relevant terminal log, Console.app log, crash log, screen recording and/or screenshots. The more information you can provide, the better!

## Development

Please help me make this thing not janky! See the [this wiki page](https://github.com/johnboiles/obs-mac-virtualcam/wiki/Developing) for build instructions and tips & tricks for developing.

## License

As the goal of this repo is to eventually get merged into [obsproject/obs-studio](https://github.com/obsproject/obs-studio/) (or die because someone made a better implementation), the license for this code mirrors the GPLv2 license for that project.
