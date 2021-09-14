cmake_minimum_required(VERSION 3.10)

set(project_name libgraph)
file(GLOB src *.cpp)

project(${project_name})

include_directories(
    ${project_name}
    PUBLIC
    ../include
)

add_library(${project_name} SHARED ${src})
