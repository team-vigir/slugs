add_library(util
  cpu_time.c cpu_stats.c safe_mem.c strsav.c texpand.c
  ptime.c prtime.c pipefork.c pathsearch.c stub.c datalimit.c
  util.h
)

target_include_directories(util INTERFACE
 "${CMAKE_CURRENT_SOURCE_DIR}"
)

install(TARGETS util DESTINATION lib)
install(FILES util.h DESTINATION "include/util")