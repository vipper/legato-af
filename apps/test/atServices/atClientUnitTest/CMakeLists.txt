#*******************************************************************************
# Copyright (C) Sierra Wireless Inc.
#*******************************************************************************

set(TEST_EXEC atClientUnitTest)
set(TEST_SOURCE "${LEGATO_ROOT}/apps/test/atServices/atClientUnitTest/")

set(LEGATO_AT_SERVICES "${LEGATO_ROOT}/components/atServices")
set(LEGATO_FRAMEWORK_SRC "${LEGATO_ROOT}/framework/c/src")

set(MKEXE_CFLAGS "-fvisibility=default -g $ENV{CFLAGS}")

if(TEST_COVERAGE EQUAL 1)
    set(CFLAGS "--cflags=\"--coverage\"")
    set(LFLAGS "--ldflags=\"--coverage\"")
endif()

mkexe(${TEST_EXEC}
    ${TEST_SOURCE}
    -i ${LEGATO_FRAMEWORK_SRC}
    -i ${LEGATO_AT_SERVICES}/Common
    ${CFLAGS}
    ${LFLAGS}
    -C ${MKEXE_CFLAGS}
)

add_test(${TEST_EXEC} ${EXECUTABLE_OUTPUT_PATH}/${TEST_EXEC})
