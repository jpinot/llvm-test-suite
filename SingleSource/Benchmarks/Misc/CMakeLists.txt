include(CheckSymbolExists)

list(APPEND LDFLAGS -lm )
list(APPEND CFLAGS -Wno-implicit-int)
set(FP_TOLERANCE 0.001)
set(Source
  lowercase.c
  mandel.c
  oourafft.c
)
if(NOT ARCH STREQUAL "K1C")
  if(NOT ARCH STREQUAL "PowerPC" OR NOT TARGET_OS STREQUAL "Darwin")
    list(APPEND Source dt.c)
  endif()
  list(APPEND Source
    revertBits.c # 1500s timeout
    perlin.c # 1500s timeout
    flops-4.c # 1500s timeout
    flops-5.c # 1500s timeout
    richards_benchmark.c # 1500s timeout
    evalloop.c # 1500s timeout
    pi.c # 1500s timeout
    flops-1.c # 1500s timeout
    flops-2.c # 1500s timeout
    flops-7.c # 1500s timeout
    mandel-2.c # 1500s timeout
    matmul_f64_4x4.c # 1500s timeout
    himenobmtxpa.c # 1500s timeout
    salsa20.c # 1500s timeout
    flops-3.c # 1500s timeout
    flops-6.c # 1500s timeout
    flops.c # 1500s timeout
    flops-8.c # 1500s timeout
    whetstone.c # 1500s timeout
    fp-convert.c # 1500s timeout
    ffbench.c # 1500s timeout
    ReedSolomon.c # 1500s timeout
    fbench.c # 1500s timeout
)
endif()
if(ARCH STREQUAL "AArch64")
  if(TARGET_OS STREQUAL "Darwin")
    file(WRITE ${CMAKE_CURRENT_BINARY_DIR}/CheckHasAArch64FMV.h "void __init_cpu_features_resolver(void);")
    check_symbol_exists(__init_cpu_features_resolver ${CMAKE_CURRENT_BINARY_DIR}/CheckHasAArch64FMV.h HAS_AARCH64_FMV)
    if(HAS_AARCH64_FMV)
      list(APPEND CFLAGS -DHAS_DARWIN_FMV)
      list(APPEND Source aarch64-init-cpu-features.c)
    endif()
  elseif(TARGET_OS STREQUAL "Linux")
    file(WRITE ${CMAKE_CURRENT_BINARY_DIR}/CheckHasAArch64FMV.h "void __init_cpu_features(void);")
    check_symbol_exists(__init_cpu_features ${CMAKE_CURRENT_BINARY_DIR}/CheckHasAArch64FMV.h HAS_AARCH64_FMV)
    if(HAS_AARCH64_FMV)
      list(APPEND CFLAGS -DHAS_LINUX_FMV)
      list(APPEND Source aarch64-init-cpu-features.c)
    endif()
  endif()
endif()
if(ARCH STREQUAL "K1C")
  list(REMOVE_ITEM Source
    mandel.c # error: '__builtin_choose_expr' requires a constant expression
  )
endif()

llvm_singlesource()
