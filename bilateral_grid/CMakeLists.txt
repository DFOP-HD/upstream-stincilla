anydsl_runtime_wrap(BILATERAL_GRID_PROGRAM
    FRONTEND "artic"
    CLANG_FLAGS ${CLANG_FLAGS}
    ARTIC_FLAGS ${ARTIC_FLAGS}
    FILES ../${BACKEND_FILE} ../utils.impala mapping_${DEVICE}.impala bilateral_grid.impala)
add_executable(bilateral_grid main.cpp ${BILATERAL_GRID_PROGRAM})
target_link_libraries(bilateral_grid ${AnyDSL_runtime_LIBRARIES})
set_target_properties(bilateral_grid PROPERTIES CXX_STANDARD 11 CXX_STANDARD_REQUIRED ON)
add_test("bilateral_grid" bilateral_grid)
configure_file(../common/lena.pgm ${CMAKE_CURRENT_BINARY_DIR}/lena.pgm COPYONLY)
