# Version minimale de CMake
cmake_minimum_required(VERSION 3.14)

# Nom du projet
project(Thive LANGUAGES CXX VERSION 1.0)

# Définir la version de C++ utilisée
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Activer les avertissements stricts (optionnel mais recommandé)
if (MSVC)
    add_compile_options(/W4)
else()
    add_compile_options(-Wall -Wextra -pedantic -Werror)
endif()

# Détection des fichiers sources
file(GLOB_RECURSE SOURCES src/*.cpp)

# Définition de l'exécutable principal
add_executable(Thive ${SOURCES})

find_package(yaml-cpp REQUIRED)

add_executable(YamlParser ${SOURCES})
target_link_libraries(YamlParser yaml-cpp)

# Optionnel : Messages pour aider à la configuration
message(STATUS "CMake success for Thive.")
