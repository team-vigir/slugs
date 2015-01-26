add_library(st
  st.c
  st.h
)

target_include_directories(st INTERFACE
 "${CMAKE_CURRENT_SOURCE_DIR}"
)

target_include_directories(st PRIVATE
             $<TARGET_PROPERTY:util,INTERFACE_INCLUDE_DIRECTORIES>
             $<TARGET_PROPERTY:mtr,INTERFACE_INCLUDE_DIRECTORIES>)


install(TARGETS st DESTINATION lib)
install(FILES st.h DESTINATION "include/st")