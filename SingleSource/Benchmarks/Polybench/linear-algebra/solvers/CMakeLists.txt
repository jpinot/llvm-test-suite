<<<<<<< HEAD
add_subdirectory(cholesky)
add_subdirectory(durbin)
add_subdirectory(gramschmidt)
add_subdirectory(lu)
add_subdirectory(ludcmp)
add_subdirectory(trisolv)
=======
if(NOT ARCH STREQUAL "K1C")
  add_subdirectory(dynprog)
  add_subdirectory(durbin)
  add_subdirectory(gramschmidt)
endif()
add_subdirectory(lu)

>>>>>>> 6f574519a ([k1c] Add compiling tests from SingleSource/Benchmarks)
