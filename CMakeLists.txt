cmake_minimum_required(VERSION 3.18)

project("llama-playground")

find_package(Llama REQUIRED)

if(Llama_FOUND)
    message(STATUS "Llama_FOUND YES ${LLAMA_INCLUDE_DIR}")
else()
    message(STATUS "Llama_FOUND NO")
endif()

add_executable(${PROJECT_NAME}
    "src/main.cpp"
    "src/common/common.cpp"
    "src/common/common.h"
    "src/common/base64.hpp"
    "src/common/console.cpp"
    "src/common/grammar-parser.cpp"
    "src/common/grammar-parser.h"
    "src/common/json.hpp"
    "src/common/ngram-cache.h"
    "src/common/stb_image.h"
    "src/common/json-schema-to-grammar.cpp"  
    "src/common/log.h"
    "src/common/sampling.cpp"
    "src/common/train.cpp"  
    "src/common/json-schema-to-grammar.h"
    "src/common/ngram-cache.cpp"
    "src/common/sampling.h"
    "src/common/train.h"
)
include_directories(${LLAMA_INCLUDE_DIR})

target_link_libraries(${PROJECT_NAME} llama)
target_link_options(${PROJECT_NAME} PRIVATE "-static")
