# grafika-hf-template

<div align="center">
    <picture>
        <img src="./green_triangle.png" width="50%" alt="An unofficial template project for BME VIK Computer Graphics homeworks">
    </picture>

An unofficial template project for BME VIK Computer Graphics homeworks
</div>

[![Build](https://github.com/levy04/grafika-hf-template/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/levy04/grafika-hf-template/actions/workflows/ci.yml)
[![Casual Maintenance Intended](https://casuallymaintained.tech/badge.svg)](https://casuallymaintained.tech/)

## Dependencies

- A C++17 compatible compiler
- [Meson](https://mesonbuild.com/Getting-meson.html) and Ninja

> [!NOTE]
> This project uses [WrapDB](https://mesonbuild.com/Wrap-dependency-system-manual.html) to manage the OpenGL dependencies. This means depending on your system, you might have to compile GLFW or GLM. If you wish to avoid this, look into installing these two in other ways.

### Windows

Follow the Meson [guide](https://mesonbuild.com/Getting-meson.html) on how to download and get started with Meson, or simply download the MSI from their latest [releases](https://github.com/mesonbuild/meson/releases) page.

### Ubuntu

Run the following command to get Meson and ninja.

```bash
sudo apt-get update && sudo apt-get install -y python3 ninja-build meson
```

### MacOS

Run the following command to get Meson and ninja.

```bash
brew install meson ninja
```

## Usage

First, use this project as a template to get your own repository. Make sure to make it private. Alternatively, you can download this repository as a zip file, and copy paste it into your main project.

Make sure to write all your code in the `src.cpp` file, since JPorta is setup such that only one file is submittable. 

Set your project up with the `meson setup build` command, after which you can compile your code with `meson compile -C build`. This will generate an executable located at `./build/out`. After initial project setup, you can recompile any time with `meson compile -C build` or `ninja -C build`. If you want a clean build, issuing `meson setup build --wipe` will regenerate the build directory.

If you are using Visual Studio Code, there is an included `launch.json` and `tasks.json` to automate the compiling process, usually pressing `F5` will work on most setups. You will still need to initially run `meson build`.

To get more familiar with Meson, you can read the [manual](https://mesonbuild.com/Manual.html), or look at some [samples](https://mesonbuild.com/Meson-sample.html).

## Notes

### Outdated framework

As the semesters go on, new versions of `framework.cpp` and `framework.h` may be released, or the framework may change entirely, and require seperate dependencies. If you notice any discrepancies, please open an Issue.

### MSVC quirks

Since the lecturer (most likely) uses MSVC to compile the submitted homeworks, the `framework.h` file has a hard-coded check for the `_HAS_CXX17` flag. As far as I know, this flag is only defined by MSVC, so gcc and clang users couldn't build their projects without either modifying `framework.h` or manually defining that flag.

This project chose to manually define the `_HAS_CXX17` flag, so that the `framework.h` file remains unmodified, and as close as possible to the internal framework used to compile the homeworks.

### Building GLFW and GLM

If you don't have GLFW or GLM installed on your system, Meson will pull them in as submodules and try to compile them. On most systems, this should Just Work™, but just in case, here are some packages that you might need:

```bash
sudo apt-get install libx11-dev libxrandr-dev libxinerama-dev libxcursor-dev libxi-dev libxext-dev libwayland-dev libxkbcommon-dev wayland-protocols
```

If you get stuck, or feel like a package is missing, please open an Issue!
