set(CLIENT_INCLUDE ${CMAKE_CURRENT_SOURCE_DIR}/src)
set(STORAGE_INCLUDE ${CMAKE_CURRENT_SOURCE_DIR}/../libstorage/src)
set(SERVICE_INCLUDE ${CMAKE_CURRENT_SOURCE_DIR}/../service/src)
set(PROXY_INCLUDE ${CMAKE_CURRENT_SOURCE_DIR}/../service/src)
set(HASH_CTX_INCLUDE "/usr/local/include/secp256k1.h")
set(MHASH_INCLUDE "/usr/local/include/secp256k1_multiset.h")

include_directories(${CLIENT_INCLUDE} ${STORAGE_INCLUDE} ${SERVICE_INCLUDE} 
                    ${PROXY_INCLUDE} ${HASH_CTX_INCLUDE} ${MHASH_INCLUDE})
