## Dependencies
You have to install ```brew install FiloSottile/musl-cross/musl-cross``` first. `musl-cross` is a GitHub project providing pre-built cross-compilation toolchains using musl libc. It allows developers to easily create statically linked, portable binaries for various architectures, which is useful for minimal applications, embedded systems, and containers.


## Build Command
```sh
  CC=x86_64-linux-musl-gcc \
  CXX=x86_64-linux-musl-g++ \
  GOARCH=amd64 \
  GOOS=linux \
  CGO_ENABLED=1 \
  go build -ldflags "-linkmode external -extldflags -static"
```

### Explaination:


1. `CC=x86_64-linux-musl-gcc`: Sets the C compiler to use the musl-based GCC for x86_64 Linux.

2. `CXX=x86_64-linux-musl-g++`: Sets the C++ compiler to use the musl-based G++ for x86_64 Linux.

3. `GOARCH=amd64`: Specifies the target architecture as 64-bit x86 (AMD64).

4. `GOOS=linux`: Sets the target operating system to Linux.

5. `CGO_ENABLED=1`: Enables cgo, allowing Go to call C code.

6. `go build`: The actual Go build command.

7. `-ldflags "-linkmode external -extldflags -static"`: 
   - `-linkmode external`: Uses external linking mode.
   - `-extldflags -static`: Passes the `-static` flag to the external linker, resulting in a statically linked binary.

This command compiles a Go program using the musl C library toolchain, targeting 64-bit Linux, with all dependencies statically linked into the final binary. 


### Reference

[https://www.afox.dev/posts/compiling-go-for-synology-nas](Ref)