# Basic iOS Theme Guide, da Clock app!
IKR very funny a whole guide for the clock app

You may be noticing your clock app not theming properly, here's a short guide to fix

## 1) Folder Structure

We're gonna need an already created theme for this, if you haven't already you can make that from [Theming Icons](https://github.com/flowerible/guides/blob/main/Theming/Theming%20Icons.md) guide :3

We're gonna need to add another folder to your `.theme` folder, call it `Bundles`

It's gonna look like this

```diff
+ ThemeName.theme
+ ├── Bundles
+ ├── IconBundles
* └── Info.plist
```

![00FF00](https://via.placeholder.com/15/00FF00/000000?text=+) Green = Folders

We're also gonna need another folder!

Create a folder named `com.apple.springboard` in your `Bundles` folder from before, it should look like this now:

```diff
+ ThemeName.theme
+ └── Bundles
+ |   └── com.apple.springboard
+ ├── IconBundles
* └── Info.plist
```

## 2) Preparing Icons

Assuming to made a clock icon already, copy that image and paste it into your `com.apple.springboard` 3 times
- Make sure they're `.png` like we explained with the other guide

We're gonna need 3 different name for these:
- `ClockIconBackgroundSquare.png`
- `ClockIconBackgroundSquare~iPhone.png`
- `ClockIconBackgroundSquare~iPad.png`

Once done, you should have something similar

```diff
+ ThemeName.theme
+ └── Bundles
+ |   └── com.apple.springboard
* |       ├── ClockIconBackgroundSquare.png
* |       ├── ClockIconBackgroundSquare~iPhone.png
* |       └── ClockIconBackgroundSquare~iPad.png
+ ├── IconBundles
* └── Info.plist
```

YAY! You did it!

## 3) Closing notes

This is assuming you've already made a theme and know the basic's on making your `.deb` file, hopefully this helped!
