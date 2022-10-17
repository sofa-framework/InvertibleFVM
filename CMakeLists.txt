cmake_minimum_required(VERSION 3.12)
project(InvertibleFVM VERSION 0.1)


set(HEADER_FILES
    InvertibleFVMForceField.h
    InvertibleFVMForceField.inl
    config.h
)

set(SOURCE_FILES
    InvertibleFVMForceField.cpp
    initPlugin.cpp
)

set(README_FILES InvertibleFVM.txt)

find_package(Sofa.Config REQUIRED)
sofa_find_package(Sofa.Component.Topology.Container.Grid REQUIRED)

add_library(${PROJECT_NAME} SHARED ${HEADER_FILES} ${SOURCE_FILES} ${README_FILES})

target_link_libraries(${PROJECT_NAME} Sofa.Component.Topology.Container.Grid)

sofa_generate_package(
    NAME ${PROJECT_NAME}
    TARGETS ${PROJECT_NAME}
    VERSION ${PROJECT_VERSION}
    RELOCATABLE "plugins"
)
