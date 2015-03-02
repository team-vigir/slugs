# find out if we are in a 32 or 64 bits platform
if(CMAKE_SIZEOF_VOID_P EQUAL 8)
	message(STATUS "Building on 64 bits")
	set(CMAKE_C_FLAGS "-mtune=native -DHAVE_IEEE_754 -DBSD -DSIZEOF_VOID_P=8 -DSIZEOF_LONG=8")
else()
	message(STATUS "Building on 32 bits")
	set(CMAKE_C_FLAGS "-mtune=native -malign-double -DHAVE_IEEE_754 -DBSD")
endif()

add_subdirectory(util)
add_subdirectory(mtr)
add_subdirectory(st)
add_subdirectory(epd)
add_subdirectory(dddmp)
add_subdirectory(cudd)
add_subdirectory(obj)

# Extras
# target_include_directories(cudd PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})