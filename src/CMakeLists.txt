
set(SOURCE_FILES
  groestl.c
  pattern.c
  util.c
  vanitygen.c
)

set(SOURCE_HEADERS
  pattern.h
  sph_groestl.h
  sph_types.h
  ticker.h
  util.h
)

if(WIN32)
  list(APPEND SOURCE_FILES winglue.c)
  list(APPEND SOURCE_HEADERS winglue.c)
endif()

add_executable(
  ${PROJECT_NAME}
  ${SOURCE_FILES}
  ${SOURCE_HEADERS}
)

target_link_libraries(
  ${PROJECT_NAME}
  ${OPENSSL_LIBRARIES}
)

target_link_libraries(
  ${PROJECT_NAME}
  ${PCRE_LIBRARIES}
)
