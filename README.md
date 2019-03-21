Welcome to HLAPI-ex, which is the same sad, unloved HLAPI found on bitbucket and now in the Unity Package manager...BUT! There are a few cherry-picked fixes based on PRs from the old bitbucket repo. Clearly there are many more problems lurking in this code, including other PRs I didn't add. Some of them were of dubious or disputed quality. Others seeminly OK, yet still produced runtime errors. Still others have probably come in while I paused my own HLAPI work. The fixes here were necessary or improved performance in my case. I haven't gone looking for major fixes to architectural issues or dumb mistakes. Instead, the idea is to use HLAPI for prototyping and patch as needed for those purposes. New tests have not been added at this point. AFAIK the tests run in Host mode (fact check me or alternative options please,) which means they'd unable to test a lot of real-world issues such as the authority-related bugs in NetworkIdentity and NetworkTransform. 

If you're here, you may know what a pain it has historically been to apply your own fixes to the HLAPI, so it's wonderful that, deprecated though it may be, it's now available as a package as of 2019.1. This means you can do what I've done here, and put a copy of this  repo on github and then reference it from your /Packages/manifest.json file. LotteMakesStuff has a good example I couldn't be bothered to reproduce here at this time.

### NOTE!!!  HEY GREAT NEWS! The 1.0.2 HLAPI package fixes the previous build issues! These fixes have been merged to master here. :)

I'm not expecting to spend much time on this, but on the off chance you find yourself actually wanting to use HLAPI (there are reasons, just DO NOT ask me what they are) and don't want to reach all the way over to the corner and press "Fork", feel free to reference this repo from your Package Manager. You can even submit PRs, ask questions, and let me know if I do something in a less than ideal way. But be nice. I'm the shy, sensitive programmer-type from the '80s or something.


---Resume the OG Unity Readme here---
# README #

The Unity Multiplayer High Level API is the open source component of the Unity Multiplayer system, this was formerly a Unity extension DLL with some parts in the engine itself, now it all exist in a package. In this package we have the whole networking system except the NetworkTransport related APIs and classes. This is all the high level classes and components which make up the user friendly system of creating multiplayer games. This document details how you can enable or embed the package and use it in your games and applications.

### What license is the Unity Multiplayer HLAPI package shipped under? ###
Unity Multiplayer HLAPI package is released under an MIT/X11 license; see the LICENSE.md file.

This means that you pretty much can customize and embed it in any software under any license without any other constraints than preserving the copyright and license information while adding your own copyright and license information.

You can keep the source to yourself or share your customized version under the same MIT license or a compatible license.

If you want to contribute patches back, please keep it under the unmodified MIT license so it can be integrated in future versions and shared under the same license.

### How do I get started? ###
* Go to the Package Manager UI in the Unity editor (found under the Window menu).
* Make sure "Show preview packages" is enabled in the Advanced menu in the package manager UI.
* The HLAPI package should appear in the list of packages, select it and click the Install button

or

* Add the package to your project manifest.json file, located in the Packages folder. Under dependencies add the line _"com.unity.multiplayer-hlapi": "0.2.6-preview"_ to the list of packages. A specific version needs to be chosen.

or

* Clone this repository into the Packages folder.

### Running tests ###

When the package files are directly included in the Packages folder of the projects (or somewhere in the Assets folder), the tests will appear and can be executed. 

When including the package via the manifest.json file the `testable` field needs to be added:

```
{
  "dependencies": {
    "com.unity.multiplayer-hlapi": "0.2.6-preview",
    ... more stuff...
  },
  "testables": [
    "com.unity.multiplayer-hlapi"
  ]
}
```

where there referenced package number should be the latest or whatever version is being tested.

When the package is included for the first time, it will be compiled, and some of the test will fail to run since the weaver has not had a chance to run yet. Triggering a recompile should fix that, for example by reimporting some script or triggering a build.

### Will you be taking pull requests? ###
We'll consider all incoming pull requests that we get. It's likely we'll take bug fixes this way but anything else will be handled on a case by case basis. Changes will not be applied directly to this repository but to an internal package repository which will be periodically synchronized with this one.
