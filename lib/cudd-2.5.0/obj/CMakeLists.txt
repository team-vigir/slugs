add_library(cuddobj
  cuddObj.cc
  cuddObj.hh
)

target_include_directories(cuddobj INTERFACE
 "${CMAKE_CURRENT_SOURCE_DIR}"
)

target_include_directories(cuddobj PRIVATE
             $<TARGET_PROPERTY:cudd,INTERFACE_INCLUDE_DIRECTORIES>)

target_link_libraries(cuddobj cudd)

add_executable(testobj testobj.cc)
target_link_libraries(testobj cuddobj)

install(TARGETS cuddobj DESTINATION lib)
install(FILES cuddObj.hh DESTINATION "include/obj")