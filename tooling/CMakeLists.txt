cmake_minimum_required(VERSION 3.15)

set(ProjectName MetaReflectTooling)

project(${ProjectName})

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

file(GLOB_RECURSE SOURCES "./*.cpp" "./*.h")

add_executable(${ProjectName} ${SOURCES})

if(MSVC)
    set_property(TARGET ${ProjectName} PROPERTY MSVC_RUNTIME_LIBRARY "MultiThreadedDLL")
endif()

target_link_libraries(${ProjectName}
    PRIVATE
    libclang
    clangTooling
    clangBasic
    clangASTMatchers
    clangFormat
    clangToolingInclusions
    clangFrontend
    clangDriver
    LLVMWindowsDriver
    clangParse
    clangSerialization
    clangSema
    clangAPINotes
    clangEdit
    clangAnalysis
    clangAST
    clangSupport
    LLVMFrontendHLSL
    clangToolingCore
    clangRewrite
    clangLex
    LLVMOption
    LLVMFrontendOpenMP
    LLVMScalarOpts
    LLVMAggressiveInstCombine
    LLVMInstCombine
    LLVMFrontendOffloading
    LLVMTransformUtils
    LLVMAnalysis
    LLVMProfileData
    LLVMSymbolize
    LLVMDebugInfoPDB
    LLVMDebugInfoMSF
    LLVMDebugInfoBTF
    LLVMDebugInfoDWARF
    LLVMObject
    LLVMIRReader
    LLVMBitReader
    LLVMAsmParser
    LLVMCore
    LLVMRemarks
    LLVMBitstreamReader
    LLVMMCParser
    LLVMMC
    LLVMDebugInfoCodeView
    LLVMTextAPI
    LLVMBinaryFormat
    LLVMTargetParser
    LLVMSupport
    LLVMDemangle
)

if(WIN32)
    target_link_libraries(${ProjectName}
        PRIVATE
        ws2_32
        version
    )
endif()

