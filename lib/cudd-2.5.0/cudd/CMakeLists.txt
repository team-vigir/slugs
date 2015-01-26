add_library(cudd
  cuddAPI.c cuddAddAbs.c cuddAddApply.c cuddAddFind.c cuddAddIte.c 
  cuddAddInv.c cuddAddNeg.c cuddAddWalsh.c cuddAndAbs.c 
  cuddAnneal.c cuddApa.c cuddApprox.c cuddBddAbs.c cuddBddCorr.c 
  cuddBddIte.c cuddBridge.c cuddCache.c cuddCheck.c cuddClip.c 
  cuddCof.c cuddCompose.c cuddDecomp.c cuddEssent.c 
  cuddExact.c cuddExport.c cuddGenCof.c cuddGenetic.c 
  cuddGroup.c cuddHarwell.c cuddInit.c cuddInteract.c 
  cuddLCache.c cuddLevelQ.c 
  cuddLinear.c cuddLiteral.c cuddMatMult.c cuddPriority.c 
  cuddRead.c cuddRef.c cuddReorder.c cuddSat.c cuddSign.c 
  cuddSolve.c cuddSplit.c cuddSubsetHB.c cuddSubsetSP.c cuddSymmetry.c 
  cuddTable.c cuddUtil.c cuddWindow.c cuddZddCount.c cuddZddFuncs.c 
  cuddZddGroup.c cuddZddIsop.c cuddZddLin.c cuddZddMisc.c 
  cuddZddPort.c cuddZddReord.c cuddZddSetop.c cuddZddSymm.c 
  cuddZddUtil.c
  cudd.h cuddInt.h
)

target_include_directories(cudd INTERFACE
 "${CMAKE_CURRENT_SOURCE_DIR}"
)


target_include_directories(cudd PRIVATE
             $<TARGET_PROPERTY:st,INTERFACE_INCLUDE_DIRECTORIES>
             $<TARGET_PROPERTY:epd,INTERFACE_INCLUDE_DIRECTORIES>
             $<TARGET_PROPERTY:util,INTERFACE_INCLUDE_DIRECTORIES>
             $<TARGET_PROPERTY:mtr,INTERFACE_INCLUDE_DIRECTORIES>)

##############################
# Profile unique abstraction #
##############################
target_compile_definitions(cudd PUBLIC -DDD_PROFILE_UNIQUE_ABS)



target_link_libraries(cudd mtr epd st)

install(TARGETS cudd DESTINATION lib)
install(FILES cudd.h cuddInt.h DESTINATION "include/cudd")