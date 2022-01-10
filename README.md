#   Cardinal Engine
##  Table of Contents
1.  [Introduction](#introduction)
2.  [Motivation](#motivation)
3.  [Building](#building)
4.  [Roadmap](#roadmap)
5.  [License](#license)

##  Introduction
Cardinal is a standalone, procedural generation-focused game engine written in C11 from scratch. Cardinal strives to be
feature-rich, cross platform game engine supporting Windows, Linux & MacOS.

##  Motivation
There are several game engines which are cross-platform, performant, feature-rich and constantly updated thereby making them an
ideal choice to kickstart game development. However, since these game engines are designed to faciliate all kinds of games
(2D, 3D, racing, FPS, MMORPG, et cetera) they are not always ideal choice for procedural generation. Even though there are
large number of community developed tools / plugins / libraries that implement procedural generation functions, they are mostly
often outdated or not supported anymore.

Cardinal engine strives to be a game engine that is designed exactly for this purpose. Cardinal engine focuses on procedural
content generation thereby providing a library full of functions and modules to integrate with. Cardinal engine also tries
to reduce the number of dependencies to the bare minimum i.e trying to rely on vendor provided libraries and headers.

##  Building
1.  Clone this branch (tree/main) the github repository
```sh
git clone https://github.com/0xdeadcodeba5e/cardinal.git
cd cardinal
```

2.  Create a dedicated build directory and configure the CMake project
```sh
#   Create a dedicated build directory
mkdir build
cd build

#   Configure the CMake Project
cmake -S .. -G <YOUR_FAVOURITE_GENERATOR>

3. Build the cardinal libraries
cmake --build . --target cardinal-static
```
##  Roadmap
The roadmap for this branch (tree/main) is as follows
- [X]   (PROJECT)   Initializing github repository
- [X]   (PROJECT)   Create a CMake Project for build system agnostic development
- [X]   (PROJECT)   Create README and LICENSE
- [X]   (PROJECT)   Publish the git repository to upstream origin

##  License
This project is licensed under **BSD 3-Clause License** . For more information, refer [LICENSE](LICENSE).
