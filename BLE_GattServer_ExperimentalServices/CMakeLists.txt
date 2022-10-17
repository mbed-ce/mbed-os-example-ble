# Copyright (c) 2020 ARM Limited. All rights reserved.
# SPDX-License-Identifier: Apache-2.0

add_subdirectory(mbed-os-experimental-ble-services/services/CurrentTime)
add_subdirectory(mbed-os-experimental-ble-services/services/LinkLoss)

add_executable(BLE_GattServer_ExperimentalServices source/main.cpp)

target_link_libraries(BLE_GattServer_ExperimentalServices
	mbed-os
	mbed-ble-utils
	mbed-ble)

# The build system in mbed-os-experimental-ble-services has not been upgraded to Mbed CE yet,
# so we can't use its CMake files directly (they reference targets like mbed-core that no longer exist).
# Instead, for now, we just compile the files from the submodule as part of this target.
target_sources(BLE_GattServer_ExperimentalServices PRIVATE
	mbed-os-experimental-ble-services/services/CurrentTime/source/CurrentTimeService.cpp
	mbed-os-experimental-ble-services/services/LinkLoss/source/LinkLossService.cpp)
target_include_directories(BLE_GattServer_ExperimentalServices PRIVATE
	mbed-os-experimental-ble-services/services/CurrentTime/include
	mbed-os-experimental-ble-services/services/LinkLoss/include)

mbed_set_post_build(BLE_GattServer_ExperimentalServices)
