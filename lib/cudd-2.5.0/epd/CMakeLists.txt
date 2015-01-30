add_library(epd
  epd.c
  epd.h
)

target_include_directories(epd INTERFACE
 "${CMAKE_CURRENT_SOURCE_DIR}"
)

target_include_directories(epd PRIVATE
             $<TARGET_PROPERTY:util,INTERFACE_INCLUDE_DIRECTORIES>)

install(TARGETS epd DESTINATION lib)
install(FILES epd.h DESTINATION "include/epd")