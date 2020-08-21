cmake_minimum_required(VERSION 3.0)

project(Numask LANGUAGES CXX)

set(CXX_STANDARD 11)

set(SRC_LIST src/allocator.cpp src/background.cpp src/intset.cpp 
src/nohotspot_ops.cpp src/queue.cpp src/search.cpp src/skiplist.cpp)

add_library(atomic_ops INTERFACE)
target_include_directories(atomic_ops INTERFACE atomic_ops)

add_library(libnumask SHARED ${SRC_LIST})
target_include_directories(libnumask PUBLIC include)
target_link_libraries(libnumask PUBLIC atomic_ops)
target_link_libraries(libnumask PUBLIC numa)
target_link_libraries(libnumask PUBLIC pthread)

add_library(libnumask_static STATIC ${SRC_LIST})
target_include_directories(libnumask_static PUBLIC include)
target_link_libraries(libnumask_static PUBLIC atomic_ops)
target_link_libraries(libnumask_static PUBLIC numa)
target_link_libraries(libnumask_static PUBLIC pthread)


add_executable(test benchmark/test.cpp)
target_link_libraries(test PUBLIC libnumask)
target_include_directories(test PRIVATE .)
target_compile_definitions(test PRIVATE LOCKFREE)