<<<<<<< HEAD
add_subdirectory(deriche)
add_subdirectory(floyd-warshall)
add_subdirectory(nussinov)
=======
if(NOT ARCH STREQUAL "K1C")
  add_subdirectory(floyd-warshall) # 1500s timeout
  add_subdirectory(reg_detect) # 1500s timeout
endif()
>>>>>>> 6f574519a ([k1c] Add compiling tests from SingleSource/Benchmarks)
