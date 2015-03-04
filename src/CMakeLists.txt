project( slugs )

cmake_minimum_required( VERSION 2.6 )

add_definitions ( -Wall )
add_definitions ( -D USE_CUDD )

set ( BDDFLAGS "-mtune=native -malign-double -DHAVE_IEEE_754 -DBSD -DCUDD_COMPILER_OPTIONS_SET" ) # hardcoded for x86_64
add_definitions ( ${BDDFLAGS} )

set ( CMAKE_BUILD_TYPE Debug )
set ( CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g -std=gnu++0x -Wall -Wextra ${BDDFLAGS}")

include_directories ( ../lib/cudd-2.5.0/include BFAbstractionLibrary )

set ( slugs_HDRS
	BFAbstractionLibrary/BF.h
	BFAbstractionLibrary/BFCudd.h
	gr1context.hpp
	variableTypes.hpp
	variableManager.hpp
	extensionExtractExplicitStrategy.hpp
	extensionRoboticsSemantics.hpp
	extensionWeakenSafetyAssumptions.hpp
	extensionBiasForAction.hpp
	extensionComputeCNFFormOfTheSpecification.hpp
	extensionCounterstrategy.hpp
	extensionExtractExplicitCounterstrategy.hpp
	extensionIncrementalSynthesis.hpp
	extensionFixedPointRecycling.hpp
	extensionInteractiveStrategy.hpp
	extensionIROSfastslow.hpp
	extensionAnalyzeInitialPositions.hpp
	extensionAnalyzeAssumptions.hpp
	BFAbstractionLibrary/BFCuddMintermEnumerator.h
	extensionComputeInterestingRunOfTheSystem.hpp
	extensionAnalyzeSafetyLivenessInteraction.hpp
	extensionAbstractWinningTraceGenerator.hpp
	extensionInterleave.hpp
	extensionPermissiveExplicitStrategy.hpp
	extensionIncompleteInformationEstimatorSynthesis.hpp
	extensionNondeterministicMotion.hpp
	extensionExtractSymbolicStrategy.hpp
	extensionTwoDimensionalCost.hpp
	)

set ( slugs_SRCS
	main.cpp
	BFAbstractionLibrary/bddDump.cpp
	BFAbstractionLibrary/BFCuddVarVector.cpp
	BFAbstractionLibrary/BFCudd.cpp
	BFAbstractionLibrary/BFCuddManager.cpp
	BFAbstractionLibrary/BFCuddVarCube.cpp
	tools.cpp
	synthesisAlgorithm.cpp
	synthesisContextBasics.cpp
	variableManager.cpp
	BFAbstractionLibrary/BFCuddMintermEnumerator.cpp
	)

set ( slugs_LIBS
	-L../lib/cudd-2.5.0/cudd
	-L../lib/cudd-2.5.0/util
	-L../lib/cudd-2.5.0/mtr
	-L../lib/cudd-2.5.0/st
	-L../lib/cudd-2.5.0/dddmp
	-L../lib/cudd-2.5.0/epd
	-lcudd
	-ldddmp
	-lmtr
	-lepd
	-lst
	-lutil
	)

add_executable ( slugs ${slugs_SRCS} )

target_link_libraries (slugs ${slugs_LIBS})