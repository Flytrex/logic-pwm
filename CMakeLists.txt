cmake_minimum_required (VERSION 3.11)
project(pwm_analyzer)

# custom CMake Modules are located in the cmake directory.
set(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake)

include(ExternalAnalyzerSDK)

set(SOURCES 
source/PwmAnalyzer.cpp
source/PwmAnalyzer.h
source/PwmAnalyzerResults.cpp
source/PwmAnalyzerResults.h
source/PwmAnalyzerSettings.cpp
source/PwmAnalyzerSettings.h
source/PwmSimulationDataGenerator.cpp
source/PwmSimulationDataGenerator.h
)

add_analyzer_plugin(pwm_analyzer SOURCES ${SOURCES})
