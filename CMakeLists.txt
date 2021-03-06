cmake_minimum_required(VERSION 2.8.4)
set(CMAKE_TOOLCHAIN_FILE ${CMAKE_SOURCE_DIR}/cmake/ArduinoToolchain.cmake)
set(CMAKE_CXX_STANDARD 14)
set(PROJECT_NAME Agentuino_uip)

set(${PROJECT_NAME}_BOARD uno)
# set(ARDUINO_CPU)
project(${PROJECT_NAME})

include_directories(/home/ksh/Arduino/libraries/UIPEthernet)

# Define additional source and header files or default arduino sketch files
set(${PROJECT_NAME}_SRCS UIPAgentuino.cpp)
set(${PROJECT_NAME}_HDRS UIPAgentuino.h)

### Additional static libraries to include in the target.
# set(${PROJECT_NAME}_LIBS)

### Main sketch file
# set(${PROJECT_NAME}_SKETCH untitled.ino)

### Add project directories into the build
# add_subdirectory()

### Additional settings to add non-standard or your own Arduino libraries.
# For this example (libs will contain additional arduino libraries)
# An Arduino library my_lib will contain files in libs/my_lib/: my_lib.h, my_lib.cpp + any other cpp files
# link_directories(${CMAKE_CURRENT_SOURCE_DIR}//home/ksh/Arduino/libraries/)
link_directories(/home/ksh/Arduino/libraries/)

# For nested library sources replace ${LIB_NAME} with library name for each library
# set(_RECURSE true)

#### Additional settings for programmer. From programmers.txt
set(${PROJECT_NAME}_PROGRAMMER avrisp)
set(${PROJECT_NAME}_PORT /dev/ttyACM0)
set(uno.upload.speed 9600)

## Verbose build process
set(${PROJECT_NAME}_AFLAGS -v)

generate_arduino_firmware(${PROJECT_NAME})

print_board_list()
print_programmer_list()
