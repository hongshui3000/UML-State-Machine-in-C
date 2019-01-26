cmake_minimum_required (VERSION 3.5)
project("hsm_UnitTest")

SET(HSM_DIR ${CMAKE_CURRENT_SOURCE_DIR}/../src )

SET(HSM_FILE
${HSM_DIR}/hsm.c
${HSM_DIR}/hsm.h
)

SET(SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/src )

SET(SOURCE_FILES
${SOURCE_DIR}/main.cpp
${SOURCE_DIR}/catch.hpp
${SOURCE_DIR}/gmock-global.h
)

file(GLOB GMOCK "src/gmock/*.h" "src/gmock/internal/*.h")

# Setup path for testcase dir
SET(TESTCASE_DIR ${SOURCE_DIR}/cases )

set(TESTCASE_FILES
    ${TESTCASE_DIR}/hierarchical_state_transition.cpp
    ${TESTCASE_DIR}/hierarchical_test.cpp
    ${TESTCASE_DIR}/priority_test.cpp
    ${TESTCASE_DIR}/simple_test.cpp
    ${TESTCASE_DIR}/state_transition.cpp
)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../src
					${CMAKE_CURRENT_SOURCE_DIR}/src
)

add_executable(hsm_UnitTest ${HSM_FILE} ${SOURCE_FILES} ${TESTCASE_FILES} ${GMOCK})