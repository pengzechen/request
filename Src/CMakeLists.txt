
include_directories(${PROJECT_SOURCE_DIR}/include)

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)

link_directories("${PROJECT_SOURCE_DIR}/lib")
link_libraries("libssl")
link_libraries("libmysql")
link_libraries("pthreadVC2")
link_libraries("ws2_32")
link_libraries("libcrypto")
link_libraries("libxml2")
link_libraries("iconv")


# pthread 有冲突
add_definitions("-DHAVE_STRUCT_TIMESPEC")

file( GLOB main_SRC "*.h" "*.c" )

aux_source_directory(./model model_SRC)
aux_source_directory(./elr_mpl elr_mpl_SRC)
aux_source_directory(./conf conf_SRC)

#指定生成目标
add_executable(server ${main_SRC} ${model_SRC} ${elr_mpl_SRC} ${conf_SRC})