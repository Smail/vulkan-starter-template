cmake_minimum_required(VERSION 3.30)
project(VulkanTutorial)

set(CMAKE_CXX_STANDARD 26)

find_package(Vulkan REQUIRED)

# GLFW
add_subdirectory(glfw)
include_directories(glfw/include)

# GLM
add_subdirectory(glm/glm)
include_directories(glm/glm)

# GSL (Microsoft GSL)
add_subdirectory(GSL)
include_directories(GSL/include)

add_executable(VulkanTutorial main.cpp)

add_compile_options(
        $<$<CXX_COMPILER_ID:GNU>:-Werror=switch>
        $<$<CXX_COMPILER_ID:Clang>:-Werror=switch>
        $<$<CXX_COMPILER_ID:MSVC>:/we4062>
)

target_link_libraries(VulkanTutorial Microsoft.GSL::GSL glfw glm::glm Vulkan::Vulkan)
