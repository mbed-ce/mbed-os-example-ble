# Copyright (c) 2020 ARM Limited. All rights reserved.
# SPDX-License-Identifier: Apache-2.0

add_executable(BLE_SupportedFeatures source/main.cpp)
target_link_libraries(BLE_SupportedFeatures mbed-os mbed-ble-utils mbed-ble)
mbed_set_post_build(BLE_SupportedFeatures)