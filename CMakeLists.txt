cmake_minimum_required(VERSION 3.19)
cmake_policy(VERSION 3.19)

# Initialize Mbed OS build system. 
# Note: This block must be before the include of app.cmake
set(MBED_APP_JSON_PATH mbed_app.json)

include(mbed-os/tools/cmake/app.cmake)
add_subdirectory(mbed-os)

project(mbed-os-example-ble)

add_subdirectory(mbed-os-ble-utils) # for the mbed-ble-utils dependency used by each example

# Figure out what BLE component targets to link to
set(EXTRA_BLE_COMPONENT_TARGETS "")
if("BlueNRG_2" IN_LIST MBED_TARGET_LABELS)

	list(APPEND EXTRA_BLE_COMPONENT_TARGETS
		mbed-ble-cordio # note: this must appear first on the link line so that the linker can correctly resolve references
		mbed-bluenrg-2)

elseif("BlueNRG_MS" IN_LIST MBED_TARGET_LABELS)

	list(APPEND EXTRA_BLE_COMPONENT_TARGETS
		mbed-ble-cordio # note: this must appear first on the link line so that the linker can correctly resolve references
		mbed-bluenrg-ms)

endif()

add_subdirectory(BLE_Advertising)
add_subdirectory(BLE_GAP)
add_subdirectory(BLE_GattClient_CharacteristicUpdates)
add_subdirectory(BLE_GattClient_CharacteristicWrite)
add_subdirectory(BLE_GattServer_AddService)
add_subdirectory(BLE_GattServer_CharacteristicUpdates)
add_subdirectory(BLE_GattServer_ExperimentalServices)
add_subdirectory(BLE_PeriodicAdvertising)
add_subdirectory(BLE_SecurityAndPrivacy)
add_subdirectory(BLE_SupportedFeatures)

mbed_finalize_build()