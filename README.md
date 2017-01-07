# Catch

CMake Installable version of [Catch](https://github.com/philsquared/Catch) unit testing library released under the Boost Software License - Version 1.0.

# Usage

* Add project using [ExternalProject_Add](https://cmake.org/cmake/help/latest/module/ExternalProject.html), note that due 
  to build order issues the catch package won't be available to find_package in the same project. For this reason a 
  [SuperBuild](https://github.com/toomuchatonce/cmake-examples/wiki/Superbuild-with-FindPackage-for-dependencies) based setup is 
  recommended to handle dependencies.
* Add ``catch`` to your target:
    ```cmake    
    add_executable(my_test ${MY_TEST_SOURCES})

    find_package(catch NO_MODULE REQUIRED)
    target_link_libraries(my_test catch)
    ```
* Add test to CMake:
    ```cmake
    enable_testing()
    add_test(NAME MyAwesomeTest COMMAND my_test)
    ```


# References

* http://stackoverflow.com/questions/34896891/catch-lib-unit-testing-and-ctest-cmake-integration



