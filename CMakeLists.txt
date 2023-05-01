cmake_minimum_required(VERSION 3.16)
project(uuid_lib C)

set(CMAKE_C_STANDARD 11)

# Specify the include directories
include_directories(
        include
)

# Specify the compilation flags
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -nostartfiles -Wall -Wextra -Werror -Wno-pedantic -Wno-unused-parameter -Wno-unused-variable -Wno-unused-function -Wno-unused-but-set-variable -Wno-unused-but-set-parameter -Wno-unused-value -Wno-unused-result -Wno-unused-label -Wno-unused-local-typedefs -Wno-unused-const-variable -Wno-unused-macros -Wno-unused-local-typedefs -Wno-unused-const-variable -Wno-unused-macros -Wno-unused-local-typedefs -Wno-unused-const-variable -Wno-unused-macros -Wno-unused-local-typedefs -Wno-unused-const-variable -Wno-unused-macros -Wno-unused-local-typedefs -Wno-unused-const-variable -Wno-unused-macros -Wno-unused-local-typedefs -Wno-unused-const-variable -Wno-unused-macros -Wno-unused-local-typedefs -Wno-unused-const-variable -Wno-unused-macros -Wno-unused-local-typedefs -Wno-unused-const-variable -Wno-unused-macros -Wno-unused-local-typedefs -Wno-unused-const-variable -Wno-unused-macros -Wno-unused-local-typedefs -Wno-unused-const-variable -Wno-unused-macros -Wno-unused-local-typedefs -Wno-unused-const-variable -Wno-unused-macros")

# Specify the optimization flags
set(CMAKE_C_FLAGS_RELEASE "${CMAKE_C_FLAGS_RELEASE} -O3")

# Specify the sources
add_executable(uuid.library
        uuid_files/init.c
        uuid_files/main/Obtain.c
        uuid_files/main/Release.c
        uuid_files/main/UuidA.c
        uuid_files/main/FreeUuid.c
        uuid_files/main/UuidToText.c
        uuid_files/main/uuid_v1.c
        uuid_files/main/uuid_v4.c
        uuid_files/main/uuid_v5.c
        uuid_files/main/uuid_preset.c
        uuid_files/main/uuid_string.c
        uuid_files/main/store.c
)

# Copy the target to the /home/vagrant directory
add_custom_command(TARGET uuid.library POST_BUILD
        COMMAND ${CMAKE_COMMAND} -E copy $<TARGET_FILE:uuid.library> /home/vagrant
        )