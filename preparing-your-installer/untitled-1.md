---
description: Step 1
---

# Downloading the Recovery HD image

After cloning/downloading `gibMacOS`, you'll have to open the the folder where it is \(or `cd` to it if you clone it with git\). If you're using macOS or Linux, you should know how to `cd` to it through your preferred Terminal emulator. If you're a **Windows** user, follow these instructions to get to the command line inside the folder.

* Open Command Prompt/PowerShell and `cd` to where it is.
* OR open the folder where it is, press `Files` &gt; `Open Windows PowerShell`

![Windows Explorer File Menu](../gitbook/assets/image%20%281%29.png)

Now that you're inside the command prompt/powershell/terminal, we'll use gibMacOS to download the Recovery HD to be restored:

1. run `python gibMacOS.command -r -v <macos version>` and replace `<macos version>` with your target version:
   * `10.14` or `mojave` for macOS Mojave release
   * `10.13` or `"high sierra"` \(with quotes\) for macOS High Sierra release
   * For the older releases, just download the `.pkg` file directly, as they've been removed from the catalog that apple provides:
     * [Sierra](http://swcdn.apple.com/content/downloads/01/53/031-86778/pnekzincp6rkf5iu91onj1bm5mw1gotnwg/RecoveryHDUpdate.pkg)
     * [El Capitan](http://swcdn.apple.com/content/downloads/08/58/031-45768/yy0xr85ltis3a7mxuqf3zgaw7sovupckd7/RecoveryHDUpdate.pkg)
     * [Yosemite](http://swcdn.apple.com/content/downloads/21/09/031-20634/8d84o1ky5gn2agnf5kiz9eed134n7y3q4c/RecoveryHDUpdate.pkg)
       * Credit: cvad's tool
2. The software will download the recovery image, meanwhile:
   1. Plug your USB device \(USB 2.0 drive are recommended\)
   2. Backup any data \*from\* it
   3. Format it \(it will be formatted anyways later on\)

Now that's downloaded, let's move on to the USB drive making...

