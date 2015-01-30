add_library(mtr 
  mtrBasic.c 
  mtrGroup.c
  mtr.h
)

target_include_directories(mtr INTERFACE
 "${CMAKE_CURRENT_SOURCE_DIR}"
)

target_include_directories(mtr PRIVATE
             $<TARGET_PROPERTY:util,INTERFACE_INCLUDE_DIRECTORIES>)

target_link_libraries(mtr util)

install(TARGETS mtr DESTINATION lib)
install(FILES mtr.h DESTINATION "include/mtr")