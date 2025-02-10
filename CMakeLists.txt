cmake_minimum_required(VERSION 3.10)
project(ActIntegradora2)

# Establecer el estándar C++17
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Incluir directorios para los archivos de cabecera
include_directories(include)

# Agregar los ejecutables para el programa principal
add_executable(ActIntegradora2
    src/main.cpp
    src/kruskal.cpp
    src/tsp.cpp
    src/ford_fulkerson.cpp
    src/linear_search.cpp
)

# Configurar Google Test para las pruebas unitarias
include(FetchContent)
FetchContent_Declare(
    googletest
    URL https://github.com/google/googletest/archive/release-1.11.0.zip
)
FetchContent_MakeAvailable(googletest)

enable_testing()

# Añadir el ejecutable para las pruebas
add_executable(
    algo_tests
    tests/test_kruskal.cpp
    tests/test_tsp.cpp
    tests/test_ford_fulkerson.cpp
    tests/test_linear_search.cpp
)

# Vincular Google Test a los ejecutables de prueba
target_link_libraries(
    algo_tests
    gtest_main
)

# Descubrir pruebas con Google Test
include(GoogleTest)
gtest_discover_tests(algo_tests)
