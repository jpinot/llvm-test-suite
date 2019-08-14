<<<<<<< HEAD
add_subdirectory(adi)
add_subdirectory(fdtd-2d)
add_subdirectory(heat-3d)
add_subdirectory(jacobi-1d)
add_subdirectory(jacobi-2d)
add_subdirectory(seidel-2d)
=======
add_subdirectory(jacobi-1d-imper)
if(NOT ARCH STREQUAL "K1C")
  add_subdirectory(seidel-2d) # 1500s timeout
  add_subdirectory(fdtd-2d) # 1500s timeout
  add_subdirectory(adi) # 1500s timeout
  add_subdirectory(fdtd-apml) # 1500s timeout
  add_subdirectory(jacobi-2d-imper) # 1500s timeout
endif()
>>>>>>> 6f574519a ([k1c] Add compiling tests from SingleSource/Benchmarks)
