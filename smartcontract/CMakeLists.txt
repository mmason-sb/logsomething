cmake_minimum_required( VERSION 3.5 )
project ( "Test-App" VERSION 1.0 LANGUAGES NONE
) 

include( CTest )

add_custom_target( wast ALL COMMAND python3 -m eosfactory.build \"${CMAKE_SOURCE_DIR}\" --c_cpp_prop \"${CMAKE_SOURCE_DIR}/.vscode/c_cpp_properties.json\" )

add_test( NAME unittest1 COMMAND python3 ${CMAKE_SOURCE_DIR}/tests/unittest1.py )
add_test( NAME unittest2 COMMAND python3 ${CMAKE_SOURCE_DIR}/tests/unittest2.py )
add_test( NAME unittest3 COMMAND python3 ${CMAKE_SOURCE_DIR}/tests/unittest3.py )

# ctest -V -R ^unittest$
# ctest -V -R ^tests$