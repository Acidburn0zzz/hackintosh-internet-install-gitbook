---
description: Basically configuring it
---

# Clover and friends \[part 1\]...

For this part of the guide you'll install and prepare clover for the ramble.

1. Download the latest [Clover LZMA](https://github.com/Dids/clover-builder/releases/latest) from Dids' repo \(thanks bb ❤️\)
   1. For Windows, use 7zip to extract the LZMA and TAR inside it until you get the iso
   2. For linux, use p7zip or file roller or whatever you use, to extract the LZMA and TAR inside it until you get the iso
   3. For macOS, use `keka` \(google it\) or `The Unarchiver` \(AppStore, Free\) to extract the LZMA and TAR inside it until you get to the iso
2. Mount the ISO
   1. On windows 10, double click or Open With &gt; Windows Explorer
   2. On linux, use `mount` command with `-o loop,ro` or with `gnome-disks` by right-clicking the iso &gt; mount image 
   3. On macOS, double click
3. Copy the EFI folder from the ISO to the CLOVER USB
   1. you should have CLOVER \(USB\) &gt; EFI \(folder\) &gt; CLOVER & BOOT
4. Open CLOVER &gt; EFI &gt; CLOVER
5. delete `doc` and `OEM` and `drivers64` \(for UEFI users\), or `drivers64UEFI` \(for legacy users\) and `drivers32` and `drivers32UEFI`.
6. for UEFI users:
   * Open `drivers64UEFI`, _deled_ everything inside
   * go to `drivers-off > drivers64UEFI`, copy ApfsDriverLoader, AppleImageLoader and AptioMemoryFix to `drivers64UEFI` that we emptied earlier.
   * Download [HFSPlus.efi](https://github.com/JrCs/CloverGrowerPro/blob/master/Files/HFSPlus/X64/HFSPlus.efi)
   * Put it in drivers64UEFI
7. Go to kexts &gt; Other
   * Go to [Goldfish64's Kext Repo](https://1drv.ms/f/s!AiP7m5LaOED-mo9XA4Ml-69cwAsikQ)
   * Download these: _\[Note: Explore each folder and you'll a Zip file, get that Zip file, not the whole folder\]_
     * FakeSMC **OR** VirtualSMC \(they both emulate an SMC system, though VSMC has quality code than FSMC, do not use both\)
     * Lilu \(an arbitrary kext patcher\)
     * WhateverGreen \(has different fixes and patches for various GPU-related issues, depends on Lilu\)
     * USBInjectAll \(Injects USB information, configuration is needed\)
     * AppleALC \(AppleHDA patcher for audio injection, depends on Lilu\)
     * _\[optional, for desktop, **CRUCIAL, for laptops**\]_ VoodooPS2 \(PS2 drivers, needed for laptops\)
     * For your LAN card:
       * **AppleIntele1000** for some old cards
       * [HoRNDIS](https://github.com/midi1996/JBOG/blob/master/Extra/HoRNDIS.kext.zip?raw=true) _\[OPTIONAL IF YOU NEED NETWORK USING ANDROID\]_
       * **IntelMausiEthernet** for most Intel NICs
       * **AtherosE2200Ethernet** for some Atheros/QualcommAtheros/Killer\(some\) NICs
       * **BCM5722D** for Broadcom BCM5722 NetXtreme and NetLink family
       * **RealtekRTL8100** for 10/100 Realtek Cards
       * **RealtekRTL8111** for Gigabit Realtek Cards
         * _Note: if you're not sure, get all of them, but it **may cause issues** later on._
     * _\[Exceptionally for WiFi-only users\]_ For your compatible WiFi Card:
       * for Broadcom based chips _\(DW1550-DW1560-DW1830...\)_: AirPortBcmFixUp
       * for Atheros based chips _\(AR5B95/195/97/197, based on AR9280/AR9285 SoC\)_:
         * go to [https://github.com/RehabMan/HP-ProBook-4x30s-DSDT-Patch/archive/master.zip](https://github.com/RehabMan/HP-ProBook-4x30s-DSDT-Patch/archive/master.zip)
         * extract the zip
         * explore to `kexts`
         * get `ProbookAtheros.kext`
       * for QComAtheros: _NOPE_ - Change it \(check AR95/4XX bellow\)
       * for Intel: _NOPE_ - Change it
       * for Atheros based on _AR95XX-AR94XX_: ATH9KFixUp with proper boot argument options seen in the original github [repo](https://github.com/chunnann/ATH9KFixup) or rehabman's [fork](https://github.com/RehabMan/ATH9KFixup) \(ignore the fact that you need to install it under /S/L/E\).
8. Extract every zip
   * Note: a kexts is a macOS driver, and it's in a form of a `a_folder_name.kext`, on windows it will show as a folder, on macOS it will show as a file.
9. now copy FakeSMC.kext - Lilu.kext - WhateverGreen.kext - USBInjectAll.kext - AppleALC.kext - \[your\_ethernet\_driver\].kext \(and any extra kext you needed from above\) and put it in _**CLOVER &gt; EFI &gt; CLOVER &gt; kexts &gt; Other**_. _\[skip the sensor kexts, they may cause kernel panics, aka KP\]_
10. now you're mostly done with Clover and macOS installer preparation.

Extra note for X299 people:

You need to add `GenericUSBXHCI` kext from the kext repository above, along VoodooTSCSync if you can't enable Core Syncing in your firmware, more on that [here](https://hackintosh.gitbook.io/-r-hackintosh-vanilla-desktop-guide/gathering-kexts#usb) \[USB\] and [here](https://www.tonymacx86.com/threads/how-to-build-your-own-imac-pro-successful-build-extended-guide.229353/) \[Go to the BIOS section, as it's the most important part of that whole talk\].

## Important

You must check _**\[MUST READ\] Config.plist Basics**_ section **before** getting to \[part 2\].
