# EternalJK - Vulkan API
[![build](https://github.com/JKSunny/EternalJK/actions/workflows/build.yml/badge.svg)](https://github.com/JKSunny/EternalJK/actions/workflows/build.yml)



This fork is <u>centered</u> around improving the rendering backend, specifically focusing on adding the [Vulkan API](https://www.vulkan.org).\
Other forks or mods can incorporate the latest updates from this repository.

> **NOTE:** Changes to other areas of the codebase are kept at a minimum. \
Game logic remains untouched, except for integrating SDL2 vulkan headers and refapi, and relocating some structures from tr_types.h to the various renderers tr_local.h \
[<kbd>View list of modified files</kbd>](https://github.com/eternalcodes/EternalJK/pull/116/files)


Support Initially started by porting to [Quake-III-Arena-Kenny-Edition](https://github.com/kennyalive/Quake-III-Arena-Kenny-Edition).<br />
After that, I found [vkQuake3](https://github.com/suijingfeng/vkQuake3/tree/master/code), hence the file structure.

Lastly, I stumbled across [Quake3e](https://github.com/ec-/Quake3e).<br />
Which is highly maintained, and is packed with many additions compared to the other repositories.

Therefore the vulkan renderer is now based on Quake3e. <br />A list of the additions can be found on [here](https://github.com/ec-/Quake3e#user-content-vulkan-renderer).

## License

[![License](https://img.shields.io/github/license/eternalcodes/EternalJK.svg)](https://github.com/eternalcodes/EternalJK/blob/master/LICENSE.txt)

OpenJK is licensed under GPLv2 as free software. You are free to use, modify and redistribute OpenJK following the terms in LICENSE.txt.

## Fork branching explained

### **Master branch**
Native implemention of the Vulkan renderer module.
> **NOTE:** upstream repository ***EternalJK** is discontinued and is replaced with **[TaystJK](https://github.com/taysta/TaystJK)** - includes Vulkan*


[![master-release](https://img.shields.io/badge/Download-This_Release-brightgreen.svg)](https://github.com/JKSunny/EternalJK/releases/tag/latest/)
[![taystjk-release](https://img.shields.io/badge/Download-TaystJK_Release-cyan.svg)](https://github.com/taysta/TaystJK/releases/)

---

### **Beta branch**
Based on master, with addition of features like instanced MD3 and Ghoul2 model caching on the gpu.
> **cvar r_vbo:** Cache static surfaces: 0 - off 1 - world 2 - world + models

[![beta-release](https://img.shields.io/badge/Download-Beta-ef7b3c.svg)](https://github.com/JKSunny/EternalJK/releases/tag/latest-beta/)
[![beta-comparision-video](https://img.shields.io/badge/See-Comparison_video-yellow.svg)](https://www.youtube.com/watch?v=kZs6kEVgMok)

---

### **ImGui** (archived)
Basic implementation of [ImGui](https://github.com/ocornut/imgui) in the vulkan renderer module, [cImGui](https://github.com/cimgui/cimgui) in client, game and ui modules
> **NOTE** Release unavailable! [build binaries](https://github.com/JACoders/OpenJK/wiki/Compilation-guide) yourself from source - ***This branch is archived and unmaintained***

---

### **PBR branch**
Implementation of [PBR](https://google.github.io/filament/Filament.html#materialsystem/parameterization/standardparameters) *(Physical Based Rendering)* material system based on [Rend2](https://github.com/SomaZ/OpenJK) renderer from OpenJK \
This adds the ability to apply *normal, roughness, metallic or specular mapping*.
by introducing the [<kbd>.mtr</kbd>](https://jkhub.org/tutorials/rend2/new-shader-keywords-r98/) file extension which is an override for [<kbd>.shader</kbd>](https://jkhub.org/tutorials/skinning/basics-of-skinning-03-shaders-r192/)

> **NOTE** Incompatible with master or beta branch! cvar r_fbo and r_vbo are enabled hard-coded.

> **NOTE** Release unavailable! [build binaries](https://github.com/JACoders/OpenJK/wiki/Compilation-guide) yourself from source

[![rend2-what-is](https://img.shields.io/badge/What_is-Rend2-yellow.svg)](https://jkhub.org/forums/topic/7468-rend2-a-modern-renderer/)
[![rend2-showcase](https://img.shields.io/badge/See-Bespin_Reborn-yellow.svg)](https://jkhub.org/files/file/4164-bespin-duel-reborn/)
[![rend2-pbr-retexture](https://img.shields.io/badge/See-PBR_Retexture-yellow.svg)](https://jkhub.org/files/file/4240-jedi-academy-pbr-retexture)

---

### **PBR Inspector branch**
Combines **PBR** and **ImGui** branch. \
Began as a local codebase to inspect/debug the PBR material system implementation. \
Like well-known *game engine editors*, a basic GUI is added, renders the game in a viewport and allows inspecting the various PBR layers \
A collapsed shader preview and basic editor (WIP), profiler plus a few more bits an bobs.

*Started entity inspector, but this has been commented out.*

> **NOTE** Release unavailable! [build binaries](https://github.com/JACoders/OpenJK/wiki/Compilation-guide) yourself from source - *Initially for personal use only, but here we are*

[![pbr-inspector-video](https://img.shields.io/badge/See-Feature_video-yellow.svg)](https://www.youtube.com/watch?v=FhEhfIeFK0U&t=10s)

---

## Forks supporting Vulkan

In addition to this fork, I also have implemented the Vulkan renderer to my forks of OpenJK and JK2MV 

[![jedi-academy-openjk](https://img.shields.io/badge/Jedi_Academy-OpenJK-brightgreen.svg)](https://github.com/JKSunny/OpenJK/) - *based on beta branch* \
[![jedi-outcast-jk2mv](https://img.shields.io/badge/Jedi_Outcast_&#x2800;-JK2MV-brightgreen.svg)](https://github.com/JKSunny/jk2mv/) - *based on master branch - (Implemented modular renderer)*

## For players

Installing and running EternalJK:

1. [Download the latest release](https://github.com/JKSunny/EternalJK/releases).
2. Extract the file into the Jedi Academy `GameData` folder. For Steam users, this will be in `<Steam Folder>/steamapps/common/Jedi Academy/GameData/`.
3. Run eternaljk.x86.exe (Rename to jamp.exe for better steam support)

#### How to enable vulkan 
1. Open up the console by pressing <kbd>~ Tilde</kbd> key
2. Type "/cl_renderer rd-vulkan; vid_restart" and hit enter

## For Developers

### Contributing to EternalJK
* [Fork](https://github.com/JKSunny/EternalJK/fork) the EternalJK project on GitHub
* Create a new branch on your fork and make your changes
* Send a [pull request](https://help.github.com/articles/creating-a-pull-request) to upstream (eternaljk/master)

## Maintainers

* [eternal](https://github.com/eternalcodes)

## Contributors 
* [bucky](https://github.com/Bucky21659)
* [loda](https://github.com/videoP)
