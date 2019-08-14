if(ARCH MATCHES "x86" OR ARCH MATCHES "riscv" OR
   ARCH MATCHES "SystemZ" OR ARCH MATCHES "Mips" OR
   ARCH MATCHES "AArch64" OR ARCH MATCHES "ARM" OR
   ARCH MATCHES "LoongArch")
  add_subdirectory(gcc-c-torture)
endif()

list(APPEND LDFLAGS -lm)
<<<<<<< HEAD
list(APPEND CFLAGS -Wno-implicit-int)
=======

if(ARCH STREQUAL "K1C")
  file(GLOB Source RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} *.c)
  list(REMOVE_ITEM Source
    uint64_to_float.c # 1500s timeout
  )
endif()

>>>>>>> 6f574519a ([k1c] Add compiling tests from SingleSource/Benchmarks)
llvm_singlesource(PREFIX "Regression-C-")
