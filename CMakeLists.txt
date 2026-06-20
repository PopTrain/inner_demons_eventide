# CMakeList.txt : CMake project for inner_demons_eventide, include source and define
# project specific logic here.
#
cmake_minimum_required (VERSION 3.8)

# Enable Hot Reload for MSVC compilers if supported.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("inner_demons_eventide")

# Collect all source files recursively from the src directory
file(GLOB_RECURSE SOURCES "src/*.cpp")
file(GLOB_RECURSE HEADERS "include/*.hpp" "include/*.h")

# Add the executable with the collected files
add_executable (inner_demons_eventide ${SOURCES} ${HEADERS})

# Defne the include directory for headers
target_include_directories(inner_demons_eventide PRIVATE "${CMAKE_CURRENT_SOURCE_DIR}/include")

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET inner_demons_eventide PROPERTY CXX_STANDARD 20)
endif()

# TODO: Add tests and install targets if needed.
