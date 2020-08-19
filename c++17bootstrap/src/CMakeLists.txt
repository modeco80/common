# CMakeLists.txt for the actual program

# This is how I like to set sources, so i can just list ADD if needed
set(CPP17BOOTSTRAP_SOURCES
	main.cpp
)

add_executable(c++17bootstrap ${CPP17BOOTSTRAP_SOURCES})

target_include_directories(c++17bootstrap PRIVATE ${CMAKE_CURRENT_SOURCE_DIR})
target_include_directories(c++17bootstrap PRIVATE ${PROJECT_SOURCE_DIR}/include)

# PCH the common include
target_precompile_headers(c++17bootstrap PUBLIC ${PROJECT_SOURCE_DIR}/include/common.h)

# Enforce C++17 support
set_property(TARGET c++17bootstrap PROPERTY CXX_STANDARD 17)
set_property(TARGET c++17bootstrap PROPERTY CXX_STANDARD_REQUIRED ON)

# Link with any needed libraries
target_link_libraries(c++17bootstrap ${CMAKE_THREAD_LIBS_INIT})