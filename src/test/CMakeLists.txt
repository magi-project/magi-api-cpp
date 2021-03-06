# Set compiler settings
SET(CMAKE_CXX_FLAGS "-std=c++11 -g -Wall")

# Find required packages
FIND_PACKAGE(Boost REQUIRED COMPONENTS system filesystem unit_test_framework)

# Find test source files
FILE(GLOB magiapi_tests_source ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp)

# Include header directory
INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR}/src/api/)

# Create new executable
ADD_EXECUTABLE(tests EXCLUDE_FROM_ALL ${magiapi_tests_source})

# Link to the appropriate libraries
TARGET_LINK_LIBRARIES(tests
    magiapi
    boost_system
    boost_filesystem
    boost_unit_test_framework)

# Set different name for executable
SET_TARGET_PROPERTIES(tests PROPERTIES OUTPUT_NAME magiapi_tests)
