# CMake wrapper for AFNetworking
cmake_minimum_required(VERSION 3.8 FATAL_ERROR)
project(AFNetworking VERSION 3.2.1)

find_library(FOUNDATION_LIBRARY Foundation)
find_library(SYSTEMCONFIGURATION_LIBRARY SystemConfiguration)
find_library(SECURITY_LIBRARY Security)

add_library(AFNetworking STATIC
    ${PROJECT_SOURCE_DIR}/AFNetworking/AFHTTPSessionManager.m
    ${PROJECT_SOURCE_DIR}/AFNetworking/AFNetworkReachabilityManager.m
    ${PROJECT_SOURCE_DIR}/AFNetworking/AFSecurityPolicy.m
    ${PROJECT_SOURCE_DIR}/AFNetworking/AFURLRequestSerialization.m
    ${PROJECT_SOURCE_DIR}/AFNetworking/AFURLResponseSerialization.m
    ${PROJECT_SOURCE_DIR}/AFNetworking/AFURLSessionManager.m
)

target_compile_options(AFNetworking PUBLIC -fobjc-arc)
target_include_directories(AFNetworking PUBLIC ${PROJECT_SOURCE_DIR})
target_link_libraries(AFNetworking PRIVATE
    ${FOUNDATION_LIBRARY}
    ${SYSTEMCONFIGURATION_LIBRARY}
    ${SECURITY_LIBRARY}
)
