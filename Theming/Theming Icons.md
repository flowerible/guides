# Basic iOS Theme Guide, Icons!
This mostly took inspiration from https://pinpal.github.io/theme-guide/, but it doesn't cover some things.. So I'd like to explain them here the best I can!

## Resources

- [PinPal's Stock Identifiers](https://pinpal.github.io/stock-identifiers/)
- [Apple application BundleID's](https://support.apple.com/guide/deployment/bundle-ids-for-native-ios-and-ipados-apps-depece748c41/web)
- [Apple application BundleID's (Older)](https://developers.perfectomobile.com/display/TT/iOS+-+Default+Applications+bundle+ID%27s)
- [Appstore BundleID's](https://offcornerdev.com/bundleid.html)

## 1) Folder Structure
You'd need a correct folder structure when creating a theme, first create a folder named `name.theme`
- You can change `ThemeName` to whatever you'd like

Alright, now we will need to create more folders inside your existing one

It *should* look like this!

```diff
+ ThemeName.theme
+ ├── IconBundles
* └── Info.plist
```

![00FF00](https://via.placeholder.com/15/00FF00/000000?text=+) Green = Folders

## 2) Info.plist
This is a plist that needs to be here when making themes, or Snowboard/Anemone won't recognize it!

You can use any text editor for this, notepad would work fine

Here's what should be in the `Info.plist`, you can add more later but this is all you need if you're doing a simple theme
- You can change `ThemeName` to whatever you'd like

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
  <plist version="1.0">
  <dict>
    <key>PackageName</key>
    <string>ThemeName</string>
  </dict>
</plist
```

If you can't manage to put this in, there's an example `Info.plist` on https://pinpal.github.io/theme-guide/

## 3) Icons!
Let's start making your icons! I would recommend you do either `256x256` or `512x512`!
- `1080x1080` can slow the device down, so tone it down a little!

We would need some programs for designing, I personally use [Pixelmator iOS](https://apps.apple.com/us/app/pixelmator/id924695435), but you can use other programs too! 


You can keep them square, snowboard can automatically handle this and round them for you

## 4) Preparing Icons
You have your icons and you're looking to put them in your theme, we would need to put them in the `IconBundles` folder

But, the image names are very specific, the formatting goes like this: `bundleID-large.png`
- Make sure they're a `.png`

```diff
+ ThemeName.theme
+ ├── IconBundles
* |   ├── com.apple.Preferences-large.png
* |   └── com.apple.weather-large.png
* └── Info.plist
```

Bundle ID's are used to identify certain things on your phone, for example `com.apple.Preferences` is the Settings app!

You can go to the [Resource](Resources) section of the guide for a few sites to find Bundle ID's

## 5) Making your package
We would need to add more folders so we can make a valid `.deb` for your package managers!

You can call the folder whatever you want, just make sure it's outside your `.theme` folder. Just put it next to it for the time being
- You can change `ThemeName` to whatever you'd like

```diff
+ ThemeName.theme
+ ThemeName 
```

![00FF00](https://via.placeholder.com/15/00FF00/000000?text=+) Green = Folders

We will need to create more folders inside your new folder!

It *should* look like this!

```diff
+ ThemeName 
+ ├── DEBIAN
+ └── Library
```

Now that we got all our newly created folders we have to make the `control` file!

Create a file named `control` in the `DEBIAN` folder, 
- This file shouldn't have any file extensions to it, things like `.txt` or `.md` will not work!

In the `control` file we have to add a few things to it

```
Package: com.yourname.themename
Name: Theme Name
Version: 1.0
Architecture: iphoneos-arm
Description: A theme with beautiful icons!
Author: Your Name
Maintainer: Your Name
Section: Themes
Depends: com.anemonetheming.anemone | com.spark.snowboard

```
If you can't manage to put this in, there's an example `control` file on https://pinpal.github.io/theme-guide/

Things to consider with the `control` file:
- The version **must** be changed every time you want to push an update
- Blank at the end is necessary!

We can add more things to the control file, but this will mostly do for now

The file structure should look like this!

```diff
+ ThemeName 
+ ├── DEBIAN
* |   └── control
+ └── Library
```

We're gonna add your theme in this, create a folder called `Themes` in your `Library` folder

Copy/move your `.theme` folder into your `Themes` folder you've created

If all goes well, it *should* look like this!!

```diff
+ ThemeName 
+ ├── DEBIAN
* |   └── control
+ └── Library
+     └── Themes
+         └── ThemeName.theme
```

Once finished we would need to make our `.deb` file!! 

Use [Newterm 2](https://chariz.com/get/newterm) or SSH into your device

Then, run `dpkg -b /path/to/ThemeName`

This should output a `.deb` you can install!
- You can share this and import it to Sileo / Zebra if you desire!

Congrats you have your theme package! You can use this to upload to repo's / let other people install!

## 5) Closing notes

This was really inspired from https://pinpal.github.io/theme-guide/ :3 

There's more to theming than the homescreen icons, you should check out more if you're interested!
- [Fixing Clock App not theming](https://github.com/flowerible/guides/blob/main/Theming/Theming%20Clock.md)
- Coming soon 
- Coming soon 
