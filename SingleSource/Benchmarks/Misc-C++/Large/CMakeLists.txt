list(APPEND LDFLAGS -lm)
set(FP_ABSTOLERANCE 0.01)
set(HASH_PROGRAM_OUTPUT 1)
# Floating point contraction must be suppressed due to accuracy issues
list(APPEND CXXFLAGS -ffp-contract=off -DFMA_DISABLED=1)
list(APPEND CFLAGS -ffp-contract=off -DFMA_DISABLED=1)

if(ARCH STREQUAL "KVX")
  file(GLOB Source RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} *.cpp)
  list(REMOVE_ITEM Source
    sphereflake.cpp # error: redefinition of 'infinity' as different kind of symbol
    ray.cpp # error: redefinition of 'infinity' as different kind of symbol
  )
endif()

llvm_singlesource()
