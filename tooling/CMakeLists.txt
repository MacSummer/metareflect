set(LLVM_LINK_COMPONENTS Support)

set(LLVM_LIB_DIR "D:/Program Files/LLVM/lib")
set(LLVM_INCLUDE_DIR "D:/Program Files/LLVM/include")

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

include_directories(
    ${LLVM_INCLUDE_DIR} 
    ${CMAKE_CURRENT_SOURCE_DIR}/Third/json/include
)

link_directories(
    ${LLVM_LIB_DIR}
)


add_executable(metareflect
    reflect.cpp
    reflectedclass.cpp
    annotations.hpp
    classfinder.hpp
    reflectedclass.hpp
    utils.hpp
    utils.cpp
)

target_link_libraries(metareflect
    PRIVATE
    clangTooling
    clangBasic
    clangASTMatchers
)

