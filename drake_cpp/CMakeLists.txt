cmake_minimum_required(VERSION 3.16...3.27)

project(drake_playground
    VERSION 0.0.1
    DESCRIPTION "Drake playground"
    LANGUAGES CXX C
)

find_package(drake REQUIRED)
find_package(gflags REQUIRED)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

add_executable(example src/main.cc)
target_compile_features(example PRIVATE cxx_std_20)
target_link_libraries(
  example
  drake::drake
  gflags
)

install(TARGETS example
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
)
