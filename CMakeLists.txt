cmake_minimum_required(VERSION 3.24)
project(TinyWebServer)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_FLAGS -pthread)
#set(CMAKE_CXX_FLAGS -mysqlclient.so)

include_directories(.)
include_directories(CGImysql)
include_directories(http)
include_directories(lock)
include_directories(log)
include_directories(threadpool)
include_directories(timer)
#link_directories(/usr/lib64/mysql)
#target_link_libraries(${PROJECT_NAME} libmysqlclient.so)

add_executable(TinyWebServer
        CGImysql/sql_connection_pool.cpp
        CGImysql/sql_connection_pool.h
        http/http_conn.cpp
        http/http_conn.h
        lock/locker.h
        log/block_queue.h
        log/log.cpp
        log/log.h
        threadpool/threadpool.h
        timer/lst_timer.cpp
        timer/lst_timer.h
        config.cpp
        config.h
        main.cpp
        webserver.cpp
        webserver.h)
target_link_libraries(TinyWebServer mysqlclient)
include_directories(/usr/include/mysql/)
link_directories(/usr/include/mysql)