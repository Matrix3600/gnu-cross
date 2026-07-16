# gnu-cross

This is a simple and lightweight project for making a cross-compilation
toolchain with the GCC compiler and the GNU C library.

These [ready-to-use](https://github.com/Matrix3600/gnu-cross/releases) toolchains run on:

- Linux x86-64
- Linux ARM64

## Supported targets

| Target                        | Kernel  | Binutils | GCC    | Glibc | Mold |
|-------------------------------|:-------:|:--------:|:------:|:-----:|:----:|
| aarch64-unknown-linux-gnu     | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | 2.41 |
| arm-unknown-linux-gnueabi     | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | 2.41 |
| arm-unknown-linux-gnueabihf   | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | 2.41 |
| armv7-unknown-linux-gnueabi   | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | 2.41 |
| armv7-unknown-linux-gnueabihf | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | 2.41 |
| i586-unknown-linux-gnu        | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | 2.41 |
| i686-unknown-linux-gnu        | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | 2.41 |
| loongarch64-unknown-linux-gnu | 5.19.16 | 2.46.1   | 16.1.0 | 2.43  | 2.41 |
| m68k-unknown-linux-gnu        | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | 2.41 |
| microblazeel-xilinx-linux-gnu | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | N/A  |
| microblaze-xilinx-linux-gnu   | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | N/A  |
| mipsel-unknown-linux-gnu      | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | N/A  |
| mipsel-unknown-linux-gnusf    | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | N/A  |
| mips-unknown-linux-gnu        | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | N/A  |
| mips-unknown-linux-gnusf      | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | N/A  |
| mips64el-unknown-linux-gnu    | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | N/A  |
| mips64-unknown-linux-gnu      | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | N/A  |
| or1k-unknown-linux-gnu        | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | N/A  |
| powerpcle-unknown-linux-gnu   | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | 2.41 |
| powerpc-unknown-linux-gnu     | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | 2.41 |
| powerpc64le-unknown-linux-gnu | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | 2.41 |
| powerpc64-unknown-linux-gnu   | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | 2.41 |
| riscv32-unknown-linux-gnu     | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | 2.41 |
| riscv64-unknown-linux-gnu     | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | 2.41 |
| s390x-ibm-linux-gnu           | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | 2.41 |
| sh4-multilib-linux-gnu        | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | 2.41 |
| x86_64-unknown-linux-gnu      | 5.4.302 | 2.46.1   | 16.1.0 | 2.43  | 2.41 |

## How to use

Download the tarball from the [release page](https://github.com/Matrix3600/gnu-cross/releases).
Choose the one that corresponds to the `host` system on which the toolchain will run, and the `target` for which you want to generate executables (from the list above).

The tarball names are `<host>_<target>.tar.xz` for Linux.

Extract the tarball to `/opt/x-tools`:
```
sudo mkdir -p /opt/x-tools
sudo tar -xf <host>_<target>.tar.xz -C /opt/x-tools

export PATH="/opt/x-tools/<target>/bin:$PATH"
<target>-gcc hello.c -o hello
```

## How to build

Fork this project, activate Github Actions for the repository, and create a new tag for the release:

```
git tag <tag_name>
git push origin <tag_name>
```
This builds the files and creates a draft release.

The host architecture (on which the toolchains run) depends on the beginning of the tag name:
- "x64-" for Linux x86-64
- "arm64-" for Linux ARM64

Otherwise you can also publish a release directly.

Or build manually for your machine's architecture:
```
./scripts/make <target>
```

## License

MIT

## Acknowledgements

We would like to express our gratitude to the following individuals and projects:

- [cross-tools](https://github.com/cross-tools)
- [crosstool-ng](https://github.com/crosstool-ng/crosstool-ng)
- [gnu-libc](https://www.gnu.org/software/libc)
