cmake_minimum_required(VERSION 3.10)
project(WebServer VERSION 1.0)

include_directories(${CMAKE_CURRENT_LIST_DIR})
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# 手动指定MySQL库路径
set(MYSQL_DIR /bin)  # 修改为实际的MySQL安装路径
include_directories(${MYSQL_DIR}/include)
link_directories(${MYSQL_DIR}/lib)

add_executable(WebServer
                main.cpp
                http_conn.cpp
                log.cpp
                sql_connection_pool.cpp)

# 将MySQL库链接到你的目标
target_link_libraries(WebServer mysqlclient)
