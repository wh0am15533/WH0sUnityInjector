# WH0's Unity Injector

This started as an experiment looking for alternate injection points in Unity without using the common process methods, that Anti-Cheat functions are on the lookout for and kill your injection. So I wanted to see if I could find something to get around this and so this was developed. It's been tested with Unity version 5.5 though the latest version.

### How does it work?

It relies purely on Mono.Cecil and Reflection functions. It's tries to find an injection point within the Unity framework, when found it dynamically creates a Hook method and adds it to the class, then it searches existing methods for an appropriate trigger point, when found it injects a method call to the Hook method as the first instruction so it doesn't interfere with normal functionality. The Hook method is setup so that once the mod is injected it doesn't keep trying to load it again. It has automatic backup/restore and error detection so your game DLL's are never fucked up. If it encounter's an error it will revert back to the backup.

### How does it circumvent Anti-Cheat methods?
First by having Unity framework load our assembly, so it doesn't get detected at runtime load. Second, Unity will now contain an internal reference to your assembly. Alot of these Anti-Cheat tools rely on looking at external assemblies on their load, and by looking to see what the game already references since it okays it's own assemblies. Sometime's a Dev will specify assemblies, but that's easily overcome with Reflection. Anyhow, this makes it seem like it's a framework assembly.

Right now it's currently limited to being a static injector, but I am working on the dynamic/runtime update already, so there will be an update coming quickly.

### Usage:

To install run it from command prompt like this:

#### Install
modinjector install "PATH_TO_GAMES_DATA_FOLDER" "C:\SOME_PATH\YourMod.dll" "YourModsNamespace.ClassThatLoadMod" "YourModLoaderMethod"

#### Remove
modinjector remove "PATH_TO_GAMES_DATA_FOLDER"

I'll eventually make the source available, but for right now I'm not until I get it more complete. I don't want the fakers acting like it's theirs before I develop it fully.

Note: During testing I've noticed that when Doorstop/BepInEx fails, this works. It even worked on Cities: Skylines where you can't inject until the game is loaded. It injected right away.

So, if you have that fucking troublesome game give this a try, plus once it's 'Injected' it'll work until you remove it, so you don't have to inject every time you load the game.

![preview](https://github.com/wh0am15533/Wh0sUnityInjector/blob/master/Screenshot.png)
