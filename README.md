# onnxruntime-arm32-lib

Prebuilt **ARM32 sysroot** bundle for cross-compiling projects (e.g. ONNX Runtime) on Linux.

This repo stores one tarball:
- `onnx-sysroot-arm32.tar.gz`

Extract it and you get a consistent set of headers and libs for `arm-linux-gnueabihf`-style builds, no need to assemble a full target filesystem.

## Usage

```bash
tar -xzf onnx-sysroot-arm32.tar.gz
# produces: ./onnx-sysroot/
```

Point your toolchain or CMake at it:

```bash
cmake -S . -B build \
  -DCMAKE_SYSROOT="$PWD/onnx-sysroot" \
  -DCMAKE_C_COMPILER=arm-linux-gnueabihf-gcc \
  -DCMAKE_CXX_COMPILER=arm-linux-gnueabihf-g++
```

## Contents

The tarball includes:
- `onnx-sysroot/usr/include/**`
- `onnx-sysroot/usr/lib/**`

Run `tar -tf onnx-sysroot-arm32.tar.gz | head` to inspect.

## Notes

- This repo keeps the sysroot as an artifact; source is not included.
- If you need a different ABI (musl / hard-float settings), regenerate the sysroot.
