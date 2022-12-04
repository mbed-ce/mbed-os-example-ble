# Copyright (c) 2020 ARM Limited. All rights reserved.
# SPDX-License-Identifier: Apache-2.0

add_executable(BLE_GattServer_AddService source/main.cpp)
target_link_libraries(BLE_GattServer_AddService mbed-os mbed-ble-utils mbed-ble ${EXTRA_BLE_COMPONENT_TARGETS})
mbed_set_post_build(BLE_GattServer_AddService)