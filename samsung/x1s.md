# Android 16 QPR1 for Galaxy S20 (x1s) - Changelog
**Analysis Period:** 2025-11-02 to 2026-01-20

---

## Repository: `android_device_samsung_x1s`

**2025-11-24**
*   **Change:** `x1s: Update some soong config variables to bool type`
*   **Detail:** Changed Soong namespace variables (e.g., `TARGET_USES_CAMERA_*`) from string to boolean type for correct logical evaluation in the build system and HAL conditionals.

**2025-12-01**
*   **Change:** `x1s: Move soong_config_set to device.mk`
*   **Detail:** Relocated `soong_config_set` variable assignments to the main `device.mk` file for better build script organization.

**2025-12-12**
*   **Change:** `x1s: Switch to device-hubble makefile`
*   **Detail:** Modified `AndroidProducts.mk` to inherit from the new common `device/samsung/hubble` makefile, integrating the device into the unified "Hubble" configuration system.
*   **Change:** `x1s: Commonize fingerprint build target`
*   **Detail:** Removed the device-specific fingerprint HAL service target in favor of the common target defined in the `hubble` tree, reducing code duplication.

**2026-01-18**
*   **Change:** `x1s: Migrate camera extra ID to soong_config_set`
*   **Detail:** Moved the camera extension identifier from a hardcoded makefile variable to a dynamic Soong configuration variable for more flexible build configuration.

## Repository: `android_device_samsung_universal9830-common`

**2025-11-22**
*   **Change:** `universal9830: Update NFC firmware path variables`
*   **Detail:** Updated build variables pointing to NFC firmware files.

**2025-11-24**
*   **Change:** `universal9830: Update some soong config variables to bool type`
*   **Detail:** Updated platform-level Soong configuration variables to proper boolean type.

**2025-11-26**
*   **Change:** `universal9830: Switch to AIDL eSE HAL`
*   **Detail:** Updated the device configuration to use the new AIDL-based Secure Element HAL.
*   **Change:** `universal9830: Switch to AIDL NFC HAL`
*   **Detail:** Updated the device configuration to use the new AIDL-based NFC HAL.
*   **Change:** `universal9830: Remove eSE from manifest`
*   **Detail:** Removed the legacy HIDL Secure Element entry from the device's hardware manifest.

**2025-11-27**
*   **Change:** `universal9830: Kill AdvancedDisplay`
*   **Detail:** Removed the AdvancedDisplay feature and its configuration from the device tree.
*   **Change:** `universal9830: sepolicy: Unlabel /dev/sec-nfc`
*   **Detail:** Removed generic SELinux labeling for the NFC device node, as precise labeling is handled in the common `slsi_sepolicy`.

**2025-12-05**
*   **Change:** `universal9830: Commonize fingerprint build target`
*   **Detail:** Consolidated the fingerprint HAL build target for all `universal9830` devices.
*   **Change:** `universal9830: init: set mask_brightness to 319`
*   **Detail:** Set a default value for the display `mask_brightness` parameter in the init script.

**2025-12-10**
*   **Change:** `universal9830: Initialize device hubble`
*   **Detail:** Added the common `device/samsung/hubble` makefile as a build dependency.
*   **Change:** `universal9830: Move NFC config to Hubble`
*   **Detail:** Moved NFC-specific configuration files to the common Hubble repository.
*   **Change:** `universal9830: Move brightness overlays to Hubble`
*   **Detail:** Moved display brightness configuration overlays to the common Hubble repository.
*   **Change:** `universal9830: Move displayLightSensorType to Hubble`
*   **Detail:** Moved the light sensor type configuration to the common Hubble repository.

**2025-12-30**
*   **Change:** `universal9830: Move some Lineage HAL features to Hubble`
*   **Detail:** Migrated various LineageOS-specific hardware feature configurations to the common Hubble repository.

**2026-01-09**
*   **Change:** `universal9830: Undefine EDEN log tag`
*   **Detail:** Removed the definition of an unused logging tag.

**2026-01-10**
*   **Change:** `universal9830: Fix eSE SPI node permissions`
*   **Detail:** Corrected the filesystem permissions (`chmod`) for the Secure Element's SPI communication node.

**2026-01-18**
*   **Change:** `universal9830: Remove recovery init from vendor`
*   **Detail:** Deleted recovery mode initialization scripts from the vendor image partition. Recovery initialization is now handled entirely by the boot image.
*   **Change:** `universal9830: Kill redundant libcrypto shim`
*   **Detail:** Removed an unnecessary compatibility library layer (shim) for `libcrypto` that was no longer required.
*   **Change:** `universal9830: Remove RIL's protobuf patch`
*   **Detail:** Removed an outdated source code patch applied to the Radio Interface Layer (RIL).
*   **Change:** `fixup! universal9830: Remove RIL's protobuf patch`
*   **Detail:** Follow-up cleanup commit for the RIL protobuf patch removal.

## Repository: `android_hardware_samsung`

**2025-11-14**
*   **Change:** `aidl: vibrator: Write use_sep_index value in constructor`
*   **Detail:** Initialized the `use_sep_index` member variable in the vibrator HAL constructor.
*   **Change:** `aidl: vibrator: Use std::vector for effect data and clean up unnecessary field initializers`
*   **Detail:** Refactored vibrator effect data handling to use `std::vector` and cleaned up redundant initializations.

**2025-11-20**
*   **Change:** `Revert "samsung: hidl: add vibrator HAL for SEC Haptic Engine"`
*   **Detail:** Reverted the addition of a custom HIDL vibrator HAL, likely due to conflicts or a change in implementation strategy.

**2025-11-23**
*   **Change:** `AdvancedDisplay: Convert for M3E support`
*   **Detail:** Updated the AdvancedDisplay module to be compatible with the M3E interface library.
*   **Change:** `doze: Convert for M3E support`
*   **Detail:** Updated the always-on-display (doze) module for M3E compatibility.
*   **Change:** `dap: Convert for M3E support`
*   **Detail:** Updated the Digital Audio Processing (dap) module for M3E compatibility.

**2025-11-24**
*   **Change:** `aidl: codec2: Switch to the real boolean values in Soong config`
*   **Detail:** Updated the AIDL Codec2 HAL to correctly use boolean values from Soong configuration.

**2025-11-25**
*   **Change:** `doze: Use new method to listen for preference changes`
*   **Detail:** Refactored the `doze` module to use a modern listener pattern for preference changes.
*   **Change:** `dap: Use new method to listen for preference changes`
*   **Detail:** Refactored the `dap` module to use a modern listener pattern for preference changes.

**2025-11-27**
*   **Change:** `dap: Properly merge with Settings category`
*   **Detail:** Integrated the `dap` settings more seamlessly into the Android Settings hierarchy.
*   **Change:** `dap: Place top intro above main switch`
*   **Detail:** Adjusted the layout of `dap` settings so the introductory text appears above the main toggle.
*   **Change:** `dap: Gray out profiles when DAP is disabled`
*   **Detail:** Improved the `dap` UI by disabling profile selections when the main feature is turned off.

**2025-12-02**
*   **Change:** `AdvancedDisplay: Apply Expressive theme`
*   **Detail:** Updated the AdvancedDisplay UI to follow the LineageOS Expressive visual theme.
*   **Change:** `doze: Apply Expressive theme`
*   **Detail:** Updated the `doze` settings UI to follow the Expressive theme.
*   **Change:** `dap: Apply Expressive theme`
*   **Detail:** Updated the `dap` settings UI to follow the Expressive theme.

**2025-12-03**
*   **Change:** `AdvancedDisplay: Blend into color preference category`
*   **Detail:** Merged AdvancedDisplay settings into the standard Android "Color & appearance" preferences menu.

**2025-12-08**
*   **Change:** `aidl: sensors: Define vintf_fragments as modules`
*   **Detail:** Correctly defined VINTF (Vendor Interface) fragments as separate modules in the sensors HAL for proper runtime manifest generation.

**2026-01-01**
*   **Change:** `Introduce pre-commit & GitHub Actions for it`
*   **Detail:** Added the `pre-commit` framework and GitHub Actions workflow for automated code quality checks.
*   **Change:** `Run \`pre-commit run --all\``
*   **Detail:** Executed the pre-commit hooks across the entire repository to apply formatting standards.
*   **Change:** `aidl: fingerprint: Add some brackets`
*   **Detail:** Added brackets to the fingerprint HAL code for better clarity and to satisfy linter rules.
*   **Change:** `ril: Run dos2unix`
*   **Detail:** Converted line endings in RIL source files from Windows (CRLF) to Unix (LF) format.

**2026-01-04**
*   **Change:** `pre-commit: Enable clang-format`
*   **Detail:** Configured the pre-commit hook to run `clang-format` for automatic code formatting.

**2026-01-13**
*   **Change:** `samsung: Remove loki_tool`
*   **Detail:** Removed the obsolete `loki_tool` used for legacy boot image patching.
*   **Change:** `samsung: Delete dtbhtoold`
*   **Detail:** Removed the deprecated `dtbhtoold` tool.
*   **Change:** `sensors: Run through clang-format`
*   **Detail:** Applied `clang-format` to the entire sensors HAL directory.
*   **Change:** `ril: Run through clang-format`
*   **Detail:** Applied `clang-format` to the entire Radio Interface Layer (RIL) directory.
*   **Change:** `rebalance_interrupts: Run through clang-format`
*   **Detail:** Applied `clang-format` to the interrupt rebalancing utility.
*   **Change:** `hidl: Run through clang-format`
*   **Detail:** Applied `clang-format` to all legacy HIDL HAL code.
*   **Change:** `aidl: Run through clang-format`
*   **Detail:** Applied `clang-format` to all modern AIDL HAL code.

**2026-01-17**
*   **Change:** `aidl: memtrack: Add some brackets`
*   **Detail:** Added clarifying brackets to the `memtrack` HAL code.
*   **Change:** `aidl: usb: Add some brackets`
*   **Detail:** Added clarifying brackets to the USB HAL code.
*   **Change:** `aidl: vibrator: Add some brackets`
*   **Detail:** Added clarifying brackets to the vibrator HAL code.

**2026-01-18**
*   **Change:** `aidl: camera: Remove deprecated module`
*   **Detail:** Removed an old, deprecated AIDL camera HAL module.
*   **Change:** `hidl: camera: Remove deprecated custom device impl and provider`
*   **Detail:** Removed the legacy custom camera device implementation and provider based on HIDL.
*   **Change:** `aidl: camera: Migrate to select()`
*   **Detail:** Refactored the AIDL camera HAL to use the `select()` system call for efficient multi-file descriptor handling, replacing less efficient polling.
*   **Change:** `aidl: usb: gadget: Migrate to select()`
*   **Detail:** Refactored the USB gadget HAL to use `select()` for better event handling.
*   **Change:** `aidl: vibrator: Migrate to select()`
*   **Detail:** Refactored the vibrator HAL to use `select()`.

## Repository: `android_hardware_samsung_slsi-linaro_config`

**2025-11-16**
*   **Change:** `hwc: Rename configurable for SAJC`
*   **Detail:** Renamed a configuration variable related to the Surface-Aware Joint Coding (SAJC) feature.
*   **Change:** `gralloc: Add configurable for SGR Gralloc`
*   **Detail:** Added a build-time configuration option for the SGR (Samsung Gralloc) implementation.
*   **Change:** `hwc: Enable USE_LIBHDR*_PLUGIN when BOARD_LIBHDR*_PLUGIN is set`
*   **Detail:** Updated the HWC (Hardware Composer) configuration to automatically enable HDR plugin usage when the corresponding board flag is set.
*   **Change:** `openmax: Rename filmgrain configurable`
*   **Detail:** Renamed a configuration variable for the film grain feature in the OpenMAX multimedia component.
*   **Change:** `openmax: Wire up ST2094 properly`
*   **Detail:** Correctly connected the configuration for the ST2094 (HDR) standard in the OpenMAX component.
*   **Change:** `config: Drop ExynosHWCService`
*   **Detail:** Removed configuration and build support for the obsolete `ExynosHWCService`.

**2025-11-17**
*   **Change:** `config: Add configurable for sbwcwrapper priority`
*   **Detail:** Added a configuration to set the priority of the SBWC (Samsung BandWidth Compressor) wrapper.
*   **Change:** `config: Add configurable for legacy libgdc option`
*   **Detail:** Added a configuration toggle for a legacy Geometric Distortion Correction (GDC) library.

**2025-11-24**
*   **Change:** `config: Update some soong config variables to bool type`
*   **Detail:** Updated core Soong configuration variables in this repository to proper boolean type.

**2025-11-26**
*   **Change:** `config: Initial configuration for s5e9925`
*   **Detail:** Added initial build configuration for the newer Exynos `s5e9925` SoC.

**2025-11-28**
*   **Change:** `config: add configurable for libhdr_header_version`
*   **Detail:** Added a configuration to specify the version of the HDR library headers.

**2025-12-04**
*   **Change:** `fixup! config: Update some soong config variables to bool type`
*   **Detail:** A follow-up commit to the boolean conversion change.

**2025-12-13**
*   **Change:** `config: Switch to SPDX license headers`
*   **Detail:** Updated all source files to use standardized SPDX license identifiers instead of full license text.

## Repository: `android_hardware_samsung_slsi-linaro_exynos`

**2025-10-26**
*   **Change:** `exynos: Add kernel-6.1-headers`
*   **Detail:** Added kernel headers for version 6.1 to support building drivers against a newer kernel ABI.

**2025-11-21**
*   **Change:** `exynos: Kill unittests`
*   **Detail:** Removed unit test code from the repository.

**2025-11-29**
*   **Change:** `exynos: add support for V4L2_PIX_FMT_NV12M_SBWCL_64_8B_FR/HAL_PIXEL_FORMAT_EXYNOS_420_SP_M_10B_64_SBWC_L_FR`
*   **Detail:** Added kernel and userspace definitions for a specific compressed pixel format (SBWC - Samsung BandWidth Compressor).

**2025-12-01**
*   **Change:** `exynos: Switch to the real boolean values in Soong config`
*   **Detail:** Updated Soong configuration variables in this repository to use proper boolean values.

## Repository: `android_hardware_samsung_slsi-linaro_graphics`

**2025-11-16**
*   **Change:** `graphics: Drop ExynosHWCService`
*   **Detail:** Removed code related to the obsolete `ExynosHWCService` from the graphics stack.
*   **Change:** `libhwc2.1: Wire up USES_VIRTUAL_DISPLAY`
*   **Detail:** Connected the build configuration for virtual display support in the HWC 2.1 library.

**2025-11-29**
*   **Change:** `graphics: add support for V4L2_PIX_FMT_NV12M_SBWCL_64_8B_FR/HAL_PIXEL_FORMAT_EXYNOS_420_SP_M_10B_64_SBWC_L_FR`
*   **Detail:** Added support for the SBWC compressed pixel format in the graphics HAL.
*   **Change:** `graphics: libhwc2.1: wire up libhdr_header_version`
*   **Detail:** Connected the HDR header version configuration to the HWC 2.1 library.

**2025-12-01**
*   **Change:** `graphics: Switch to the real boolean values in Soong config`
*   **Detail:** Updated graphics-related Soong config variables to proper boolean type.
*   **Change:** `libacryl: add support to sbwc_v2_8`
*   **Detail:** Updated the `libacryl` post-processing library to support version 2.8 of the SBWC protocol.

**2025-12-04**
*   **Change:** `libhwc2.1: Fix boolean logic in needDstBufRealloc check`
*   **Detail:** Fixed a logical error in the buffer reallocation check within the HWC 2.1 library.

## Repository: `android_hardware_samsung_slsi-linaro_interfaces`

**2025-11-17**
*   **Change:** `interfaces: Add VINTF fragment for SbwcDecompService`
*   **Detail:** Added a Vendor Interface (VINTF) manifest entry for the SBWC Decompression Service.

**2025-12-01**
*   **Change:** `interfaces: Kill EPIC HIDL`
*   **Detail:** Removed the legacy EPIC (Enhanced Performance Imaging Control) HIDL interface.

## Repository: `android_hardware_samsung_slsi-linaro_openmax`

**2025-12-01**
*   **Change:** `openmax: Switch to the real boolean values in Soong config`
*   **Detail:** Updated OpenMAX multimedia configuration variables to proper boolean type.

## Repository: `android_hardware_samsung_slsi_nfc`

**2025-11-25**
*   **Change:** `nfc: Remove the NFC HIDL HAL`
*   **Detail:** Completely removed the legacy HIDL-based NFC HAL implementation.
*   **Change:** `nfc: Rename the nfc_nci_samsung lib and the HIDL HAL`
*   **Detail:** Renamed libraries and components as part of the HIDL-to-AIDL migration cleanup.

**2025-11-26**
*   **Change:** `nfc: Decrease /dev/sec-nfc permissions`
*   **Detail:** Tightened filesystem permissions on the physical NFC device node for improved security.

## Repository: `android_device_samsung_slsi_sepolicy`

**2025-11-26**
*   **Change:** `common: Label /dev/sec-nfc`
*   **Detail:** Added precise SELinux security context labeling for the `/dev/sec-nfc` device node, allowing the NFC HAL to access the hardware.

## Repository: `android_kernel_samsung_universal9830`

**2025-09-28**
*   **Change:** `arm64: configs: Enable CONFIG_ANDROID_VENDOR_HOOKS`
*   **Detail:** Enabled the kernel configuration option that allows vendor modules to hook into core kernel events.

**2025-11-10**
*   **Change:** `fs: fuse: Pick Samsung changes from S918B`
*   **Detail:** Merged FUSE filesystem driver updates from the kernel for the Galaxy S23 (S918B).

**2025-11-20**
*   **Change:** `Update localversion-st, tree is up-to-date with 5.4.301.`
*   **Detail:** Marked the kernel as synchronized with the Linux 5.4.301 long-term stable release, incorporating numerous upstream fixes.

**2025-12-06**
*   **Change:** `arm64: configs: Enable CONFIG_FUSE_BPF`
*   **Detail:** Enabled support for FUSE-BPF, allowing userspace BPF programs to attach to FUSE operations.

**2026-01-02**
*   **Change:** `arm64: configs: Disable CONFIG_PAGE_STEAL`
*   **Detail:** Disabled the `CONFIG_PAGE_STEAL` kernel configuration option.

**2026-01-05**
*   **Change:** `drivers: input: touchscreen: Don't guard game mode for sec y79a_c`
*   **Detail:** Removed a conditional guard that was incorrectly blocking the "game mode" feature for the specific `sec y79a` touchscreen controller.

> **Note:** The kernel log contains hundreds of backported commits from upstream Linux 5.4.301. The list above highlights only the most significant device-specific or feature-related changes. The upstream merge includes critical fixes for filesystems (FUSE, EXT4), memory management, networking, and security.
