# onnxruntime-arm32-lib

Prebuilt **ARM32 sysroot** bundle for cross-compiling projects (e.g. ONNX Runtime) on Linux.

This repo stores a large tarball:
- `onnx-sysroot-arm32.tar.gz`

It is useful when you need a consistent set of headers/libs for `arm-linux-gnueabihf`-style builds, without setting up a full target filesystem.

## Usage

Extract the sysroot:

```bash
tar -xzf onnx-sysroot-arm32.tar.gz
# produces: ./onnx-sysroot/
```

Then point your toolchain/CMake to it. Example (generic):

```bash
cmake -S . -B build \
  -DCMAKE_SYSROOT="$PWD/onnx-sysroot" \
  -DCMAKE_C_COMPILER=arm-linux-gnueabihf-gcc \
  -DCMAKE_CXX_COMPILER=arm-linux-gnueabihf-g++
```

## Contents

The tarball contains:
- `onnx-sysroot/usr/include/**`
- `onnx-sysroot/usr/lib/**` (if present)

(Use `tar -tf onnx-sysroot-arm32.tar.gz | head` to inspect.)

## Notes

- This repo intentionally keeps the sysroot as an artifact; source is not included.
- If you need a different ABI (musl / hard-float settings), regenerate the sysroot accordingly.
