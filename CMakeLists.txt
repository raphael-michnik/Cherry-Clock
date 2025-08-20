cmake_minimum_required(VERSION 3.16)
project(PomodoroBasic LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Find Qt (Widgets only; keep it light).
find_package(Qt6 COMPONENTS Widgets REQUIRED)

add_executable(pomodoro
    src/main.cpp
    src/Tray.cpp
    src/TimerEngine.cpp
    src/Storage.cpp
    src/AppleBridge.cpp
    src/Tray.h
    src/TimerEngine.h
    src/Storage.h
    src/AppleBridge.h
)

target_link_libraries(pomodoro PRIVATE Qt6::Widgets)

# On macOS, make it a bundle so it can live in the menu bar nicely
if(APPLE)
    set_target_properties(pomodoro PROPERTIES
        MACOSX_BUNDLE TRUE
        MACOSX_BUNDLE_GUI_IDENTIFIER "dev.yourname.pomodoro"
        MACOSX_BUNDLE_BUNDLE_NAME "PomodoroBasic"
        MACOSX_BUNDLE_INFO_PLIST "${CMAKE_CURRENT_SOURCE_DIR}/Info.plist"
    )
endif()
