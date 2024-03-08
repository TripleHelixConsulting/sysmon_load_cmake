 
cmake_minimum_required(VERSION 3.0)

project (loadTester LANGUAGES C CXX)

set(CMAKE_SYSTEM_NAME Linux)

set(IMGUI_DIR imgui)
set(TP_DIR thread_pool)
set(ENDLESS_TH_M_DIR endlessThMngr)

set(SOURCES
    main.cpp
    K3Buffer.cpp
    K3Proc.cpp
    K3Key.cpp
    imgui_thread.cpp
    ${IMGUI_DIR}/thread_pool.cpp
    ${ENDLESS_TH_M_DIR}/endless_th_manager.cpp
    ${IMGUI_DIR}/imgui.cpp
    ${IMGUI_DIR}/imgui_demo.cpp
    ${IMGUI_DIR}/imgui_draw.cpp
    ${IMGUI_DIR}/imgui_tables.cpp
    ${IMGUI_DIR}/imgui_widgets.cpp
    ${IMGUI_DIR}/backends/imgui_impl_glfw.cpp
    ${IMGUI_DIR}/backends/imgui_impl_opengl2.cpp
)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_THREAD_SAFE_CPP ON)

find_package(X11 REQUIRED)
find_package(Threads REQUIRED)
find_package(OpenGL REQUIRED)
find_package(glfw3 REQUIRED)

set(GLFW3_DIR "/usr/lib/cmake/glfw3/glfw3Config.cmake")

#add_executable(${EXE} ${SOURCES})
add_executable(${PROJECT_NAME})
target_sources(${PROJECT_NAME} PUBLIC main.cpp)

target_link_libraries(${PROJECT_NAME} GL glfw3)

# Optional for debug builds
# if(CMAKE_BUILD_TYPE STREQUAL Debug)
#    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g")
# endif()
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g")
# Optional for warnings
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wformat")

# add_custom_target(clean COMMAND rm -f ${EXE} *.o)
