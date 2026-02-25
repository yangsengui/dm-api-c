# dm-api-c

C headers and CMake package exports for DistroMate `dm_api`.

## Build And Install

```bash
cmake -S . -B build -DCMAKE_BUILD_TYPE=Release
cmake --build build
cmake --install build --prefix <install-prefix>
```

## Consume

```cmake
find_package(dm_api_c REQUIRED)
target_link_libraries(your_target PRIVATE dm::api_c)
```

## API Groups

- Runtime and launcher lifecycle (`DM_*`)
- Activation configuration and activation flow (`Set*`, `Activate*`)
- Validation/status and info (`IsLicense*`, `Get*`)
- Version/update APIs (`DM_GetVersion`, `DM_CheckForUpdates`, `DM_DownloadUpdate`)
