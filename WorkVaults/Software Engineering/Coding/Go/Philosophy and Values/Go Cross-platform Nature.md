---
alias: cross platform, 
---
software often executed on different platforms, mac for development, linux for deployment. Often need the same code to work in a reliable, consistent manner across those different platforms. Go Supports this by having platform-specific compilers that take a common codebase and compile that to a binary that's optimisezed to run on each given platform. 

- Just need to switch environment variables to compile to a different OS target

WINDOWS
- GOOS = windows
- GOARCH = amd 64
OS X
- darwin
- amd64
Android 
- GOOS = andoid
- GOARCH = arm

