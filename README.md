# NanoMod

## Current Stable Release

9.2.20170610

## Downloads

* Stable Downloads [![Androidfilehost Link](doc/afh.png)](https://www.androidfilehost.com/?a=show&w=files&flid=150729)
* Archived Downloads [![Androidfilehost Link](doc/afh.png)](https://www.androidfilehost.com/?w=files&flid=156387)
* Snapshot
  * on GNU/Linux, MacOS or *BSD clone this repository and use the provided `mod.sh` script like
    * `mod.sh zip` for the full package
    * `mod.sh microg` for the microg only package
    * `mod.sh fdroid` for the F-Droid only package
    * `mod.sh patcher` for the on-device framework-patcher package
    * `mod.sh uninstaller` for the uninstaller package
    * `mod.sh all` for all packages at once

## Support

XDA Support Thread [![XDA Link](doc/xda.png)](https://forum.xda-developers.com/apps/magisk/module-nanomod-5-0-20170405-microg-t3584928)

## ChangeLog

ChangeLog.md [![GitHub Link](doc/github.png)](ChangeLog.md)

## Summary

**NanoMod** can be installed as a Magisk Module or directly to /system, though a bit functionality is only available with Magisk.

More information about Magisk [![XDA Link](doc/xda.png)](https://forum.xda-developers.com/apps/magisk)

NanoMod includes

* microG and it's companions
  * on-device framework-patcher for microG support (signature spoofing)
  * on-pc framework-patcher for microG support (signature spoofing)
  * both patchers create the `/system/.nanomod-patcher` file after patching
* F-Droid and it's privileged extension
* modified Play Store to allow (in-)app-purchases with microG
  * this required two steps
    * microG Gms Core and Play Store need to be signed with the same key
    * Play Store needs to be modified see the [patch](doc/Phonesky.diff)
  * alternatively Yalp Store can be installed instead
* custom init scripts
* pseudo-debloat feature (Magisk-only)
  * disables applications systemless-ly
  * pre-configured default settings
* several Open Source applications
  * include replacements for the pseudo-debloated applications
* additional components
  * GNU Bash shell
  * GNU Nano terminal editor
* The Legend of Zelda ringtones and sounds

## Packages

* **NanoMod**: includes
  * everything mentioned in the Summary
* **NanoMod-microG**: includes
  * microG and it's companions
  * GNU Bash
  * pseudo-debloat feature
  * app store
* **NanoMod-fdroid**: includes
  * F-Droid and it's privileged extension
* **NanoMod-patcher**: includes
  * on-device framework-patcher
  * creates the file `/system/.nanomod-patcher` after successful patching
* **NanoMod-uninstaller**: includes
  * uninstaller for all NanoMod Magisk Modules
* **framework-patcher.sh** (clone this repository)
  * on-pc framework-patcher
  * creates the file `/system/.nanomod-patcher` after successful patching
* **force-debloat.sh** (clone this repository)
  * system debloater
  * the list of applications resides in the script itself
  * needs to be run from TWRP, requires explicit user acceptance
* **mount-magisk.sh** (clone this repository)
  * script to mount or unmount Magisk in TWRP
  * script toggles mount-state (read: will mount Magisk if unmounted and unmount Magisk if mounted)

## Details

### NanoMod

This lists features unique to NanoMod.

#### nanomod-overlay

The `nanomod-overlay` script handles the following features

* pseudo-debloat (Magisk-only)
  * show the list of pseudo-debloated apps
  * add or remove apps from the list of pseudo-debloated apps
* grant signature spoofing permission to microG and Play Store if required
  * both in Magisk and System Mode
* issue `nanomod-overlay --help` for the full list of options

Full details on the pseudo-debloat feature [![GitHub Link](doc/github.png)](doc/PseudoDebloat.md)

#### init scripts

The following init scripts are bundled with NanoMod

* external_sd
  * symlink SD Card mount point to `/external_sd`
  * SD Card needs to be inserted upon boot
* fstrim
  * trim file systems (may increase speed)
* logscleaner
  * clean up log files
* sqlite
  * clean up sqlite databases

When in Magisk Mode the init scripts create their log files in

  `/magisk/NanoMod/.logs/${script}.log.${date}`

When installed to /system your ROM needs to support running scripts in

  `/system/etc/init.d`

or you can use **Kernel Adiutor's** init.d emulation.

### microG

microG is an Open Source replacement for Google Services, full details can be found at the microG homepage [![Web Link](doc/microg.png)](http://microg.org/)

NanoMod includes microG as follows

* microG GmsCore [![GitHub Link](doc/github.png)](https://github.com/microg/android_packages_apps_GmsCore) and Play Store [![APK Mirror Link](doc/apkmirror.png)](https://www.apkmirror.com/apk/google-inc/google-play-store/)  modified to allow (in-)app purchases
* with **Mozilla** location provider backend [![F-Droid Link](doc/fdroid.png)](https://f-droid.org/repository/browse/?fdfilter=mozilla&fdid=org.microg.nlp.backend.ichnaea)
* with **Nominatim** adress provider backend [![F-Droid Link](doc/fdroid.png)](https://f-droid.org/repository/browse/?fdfilter=nominatim&fdid=org.microg.nlp.backend.nominatim)
* with **microG** GsfProxy [![GitHub Link](doc/github.png)](https://github.com/microg/android_packages_apps_GsfProxy)
* with **microG** DroidGuard Helper [![GitHub Link](doc/github.png)](https://github.com/microg/android_packages_apps_RemoteDroidGuard)
  * required for SafetyNet support
* support for Maps API version 1
* support for Google Calendar and Contacts Sync
  * disabled by default
* choose between official **Play Store** or unofficial **Yalp Store** [![F-Droid Link](doc/fdroid.png)](https://f-droid.org/repository/browse/?fdfilter=yalp&fdid=com.github.yeriomin.yalpstore)
  * **Yalp Store** can use system permissions to install packages, so you don't need to enable `Unknown Sources`
    * got to **Yalp Store** > Settings > Installation Method > `Using system permissions`

### F-Droid and Applications

F-Droid [![F-Droid Link](doc/fdroid.png)](http://www.fdroid.org) is an app store for Open Source applications.

NanoMod includes both F-Droid and it's Privileged Extension, so you don't need to enable `Unknown Sources`.

Additionally NanoMod includes a variety of applications, check full details [![GitHub Link](doc/github.png)](doc/Applications.md)

### The Legend of Zelda ringtones and sounds

NanoMod includes **The Legend of Zelda** [![Nintendo Link](doc/zelda.png)](http://www.zelda.com/) ringtones and sounds, because it's dangerous to root alone.

Full details [![GitHub Link](doc/github.png)](doc/ZeldaSounds.md)

## Installation

### Alter Installation

NanoMod supports altering the installation settings to a certain degree.

Full details on altering installation [![GitHub Link](doc/github.png)](doc/AlterInstallation.md)

### Installation Process

#### NanoMod

* Download pre-built or create a zip file from this repository
* perform full wipe (/system, /data, /cache, Dalvik/ART cache)
  * recommended, but not required
* install desired ROM
  * make sure it does **not** include GApps if you want to use microG
  * either pre-patched with signature spoofing support or **deoxeded** so you can patch yourself (instructions follow)
* install desired Kernel (if any)
* install **Magisk**
  * recommended, but not required
  * if **Magisk** is installed, NanoMod will be installed as Magisk-Module, else it will install into `/system` directly
* install **NanoMod**
* reboot into ROM

#### microG

For **microG** to work, your ROM needs to have signature spoofing enabled (or a **deodexed** ROM to patch yourself).

If your ROM does not have signature spoofing support, you can manually patch it using either
  * the on-device framework-patcher zip
    * flash after booting into the ROM once
  * the `framework-patcher.sh` script (found in the github repository)
    * use from your PC or laptop while your device is in TWRP. This shell script for GNU Bash (and compatible shells) works on unixoid operating systems like GNU/Linux, BSD or MacOS. It automizes the process of downloading Haystack [![GitHub Link](doc/github.png)](https://github.com/Lanchon/haystack), pulling files from phone, patching and installing the modified **services.jar** on the device.

Both patchers support installing the patched services.jar into the following locations
  * NanoMod Magisk Module
  * NanoMod-microG Magisk Module
  * directly into `/system`

So you can use them regardless whether you're using NanoMod or not.

Once your ROM supports signature spoofing, you need to setup microG like this
  * go into **microG settings** and set up everything like:
    * check results in **Self-Check**, grant missing permissions (by tapping on them)
      * especially the 'Battery Optimization' item
    * enable **Google device registration**
    * enable **Google Cloud Messaging** (only if you want to receive push messages from your applications)
    * enable **Google SafetyNet** (required for applications that utilize SafetyNet, for example Pokémon GO, ...)
      * menu > set to use the official servers
    * in **UnifiedNlp Settings** choose
      * **Mozilla Location Backend** as Geolocation backend
      * **Nominatim** as Address lockup backend
    * after everything is done, reboot
    * go to **Play Store**, setup account and install your apps

## License & Credits

My own work (NanoMod itself) is licensed under the GNU General Public License version 3 or newer [![GNU Link](doc/gnu.png)](https://www.gnu.org/licenses/gpl-3.0.txt)

For more details (including authors and license) on every provided application or Software press the icon next to it.

Additional credits go to

* Mar-V-In for microG
* topjohnwu for Magisk
* Lanchon for dexpatcher and haystack
* osm0sis for GNU Nano build

Special Thanks to the beta testers

* xenithorb
* ShapeShifter499

## Issues

List of known issues

* microG DroidGuard Helper or Play Store crashing
  * there's currently an issue with **Magisk** that prevents microG DroidGuard Helper or Play Store from properly working when magic-mounted as `/system` application, see Magisk Issue 155 [![GitHub Link](doc/github.png)](https://github.com/topjohnwu/Magisk/issues/155)
  * this does not happen on all devices
  * if you are affected of this issue, instead install them as an user app, by installing the apk from
    * `/system/priv-app/DroidGuard/DroidGuard.apk` for microG DroidGuard Helper
    * `/system/priv-app/Phonesky/Phonesky.apk` for Play Store
* SafetyNet check fails with `can't connect to Google API`
  * see `microG DroidGuard Helper or Play Store crashing` above and install microG DroidGuard Helper as user application
* Play Store lacks signature spoofing permission
  * on ROMs like **crDroid** or **OmniROM**, that have built-in signature spoofing, in some cases the Play Store is not granted that permission automatically, to fix this, issue one of the following commands as **root** on your device
    * `nanomod-overlay --permission`
    * `pm grant com.android.vending android.permission.FAKE_PACKAGE_SIGNATURE`
* Battery Drain
  * microG fails to register applications  to GCM (Google Cloud Messaging) if they were installed **before** microG, but the apps keep trying to register and that causes the battery drain, all apps installed **after** microG are properly registered, to fix the battery drain either
    * do a clean flash of your ROM (,Magisk) and NanoMod and install your apps after microG setup
    * uninstall and re-install all your applications (backup application data if required)

Additional [helpful information](https://github.com/microg/android_packages_apps_GmsCore/wiki/Helpful-Information) from the microG wiki.

## FAQ

```
Q: will there be a GApps version, instead of microG?
A: no. but you can choose not to populate microG.

Q: what devices was this tested on?
A: Moto X Play (lux), Samsung Galaxy Tab 4 (matissewifi), Samsung Galaxy S6 (zeroflte)

Q: what ROMs was this tested on?
A: LineageOS, Resurrection Remix, AICP, AOSP Extended, crDroid, should work on any LineageOS / AOSP based ROM that is working with Magisk.
```
