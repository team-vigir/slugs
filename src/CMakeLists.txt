#TODO: Port SLUGS' qmake to cmake

include_directories(../lib/cudd-2.5.0/include BFAbstractionLibrary)

add_executable(slugs BFAbstractionLibrary/bddDump.cpp BFAbstractionLibrary/BFCuddVarVector.cpp BFAbstractionLibrary/BFCudd.cpp BFAbstractionLibrary/BFCuddManager.cpp \
    BFAbstractionLibrary/BFCuddVarCube.cpp tools.cpp synthesisAlgorithm.cpp synthesisContextBasics.cpp variableManager.cpp \
    BFAbstractionLibrary/BFCuddMintermEnumerator.cpp)

add_library(lcudd ../lib/cudd-2.5.0/cudd)
add_library(ldddmp ../lib/cudd-2.5.0/dddmp)
add_library(lmtr ../lib/cudd-2.5.0/mtr)
add_library(lepd ../lib/cudd-2.5.0/epd)
add_library(lst ../lib/cudd-2.5.0/st)
add_library(lutil ../lib/cudd-2.5.0/util)

target_link_libraries(slugs lcudd, lutil, lmtr, lst, ldddmp, lepd)

### From qmake Tool.pro:

# SOURCES += main.cpp BFAbstractionLibrary/bddDump.cpp BFAbstractionLibrary/BFCuddVarVector.cpp BFAbstractionLibrary/BFCudd.cpp BFAbstractionLibrary/BFCuddManager.cpp \
#     BFAbstractionLibrary/BFCuddVarCube.cpp tools.cpp synthesisAlgorithm.cpp synthesisContextBasics.cpp variableManager.cpp \
#     BFAbstractionLibrary/BFCuddMintermEnumerator.cpp

# TARGET = slugs
# INCLUDEPATH = ../lib/cudd-2.5.0/include BFAbstractionLibrary

# LIBS += -L../lib/cudd-2.5.0/cudd -L../lib/cudd-2.5.0/util -L../lib/cudd-2.5.0/mtr -L../lib/cudd-2.5.0/st -L../lib/cudd-2.5.0/dddmp -L../lib/cudd-2.5.0/epd -lcudd -ldddmp -lmtr -lepd -lst -lutil