anydsl_runtime_wrap(AOBENCH_PROGRAM
    FRONTEND "artic"
    CLANG_FLAGS ${CLANG_FLAGS}
    ARTIC_FLAGS ${ARTIC_FLAGS}
    FILES ../${BACKEND_FILE} ../utils.impala mapping_${DEVICE}.impala aobench.impala)
add_executable(aobench main.cpp ${AOBENCH_PROGRAM})
target_link_libraries(aobench ${AnyDSL_runtime_LIBRARIES})
set_target_properties(aobench PROPERTIES CXX_STANDARD 11 CXX_STANDARD_REQUIRED ON)
add_test("aobench" aobench)
