# Big Sur compatibility branch

This branch is an isolated compatibility effort for macOS Big Sur (11.x). Do not merge into `main` until the app has been built and tested on Big Sur.

## Current configuration
- CMake deployment target: macOS 11.0
- Universal build is the normal default; CI specifically builds Intel `x86_64` to match Intel MacBook Pro hardware.
- The branch Info.plist declares `LSMinimumSystemVersion=11.0`.
- The `UniformTypeIdentifiers` dependency was removed on this branch as part of earlier compatibility work. If the source still refers to `UTType` symbols, compilation will fail; CI is intended to expose that rather than hide it.

## Build remotely
Open the repository's **Actions** tab, select **Big Sur compatibility build**, then choose **Run workflow** on branch `codex/big-sur-compatibility`. If the workflow passes, download the artifact named `Nextpad-BigSur-x86_64-UNTESTED`.

A successful CI build confirms compilation and linking only. The resulting app has not been runtime-tested on macOS Big Sur. Do not replace the official app until it launches and basic editing, file dialogs, saving, syntax highlighting, and quitting have been tested on Big Sur.
