cmake_minimum_required(VERSION 3.10)


# GoogleTest requires at least C++11
set(CMAKE_CXX_STANDARD 11)
set(project_name testG02)


project(${project_name})


include(FetchContent)
FetchContent_Declare(
  googletest
  URL https://github.com/google/googletest/archive/609281088cfefc76f9d0ce82e1ff6c30cc3591e5.zip
)
# For Windows: Prevent overriding the parent project's compiler/linker settings
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)

file(GLOB test_src *.cpp)
enable_testing()


add_executable(${project_name} ${test_src})
target_include_directories(
    ${project_name}
    PUBLIC
    ../include
)
target_link_libraries(${project_name} PRIVATE libgraph gtest_main)


include(GoogleTest)
gtest_discover_tests(test_graph)
