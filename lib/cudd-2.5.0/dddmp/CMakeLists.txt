add_library(dddmp
 dddmpStoreBdd.c dddmpStoreAdd.c dddmpStoreCnf.c
 dddmpLoad.c dddmpLoadCnf.c
 dddmpNodeBdd.c dddmpNodeAdd.c dddmpNodeCnf.c
 dddmpStoreMisc.c dddmpUtil.c dddmpBinary.c dddmpConvert.c
 dddmpDbg.c 
 dddmp.h dddmpInt.h
)

target_include_directories(dddmp INTERFACE
 "${CMAKE_CURRENT_SOURCE_DIR}"
)

target_include_directories(dddmp PRIVATE
             $<TARGET_PROPERTY:cudd,INTERFACE_INCLUDE_DIRECTORIES>)


install(TARGETS dddmp DESTINATION lib)
install(FILES dddmp.h dddmpInt.h DESTINATION "include/ddmp")