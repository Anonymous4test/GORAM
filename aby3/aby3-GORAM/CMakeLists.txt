
file(GLOB_RECURSE SRCS *.cpp)
add_library(aby3-GORAM STATIC ${SRCS})

target_include_directories(aby3-GORAM PUBLIC ${CMAKE_SOURCE_DIR}) 
target_link_libraries(aby3-GORAM aby3 aby3-GORAM-Core aby3-RTR)

option(MPI_APP "Enable MPI support" OFF)

if(MPI_APP)
    target_compile_definitions(aby3-GORAM PRIVATE "MPI_APP=ON")
endif()

# global graph folder
target_compile_definitions(aby3-GORAM PUBLIC "GRAPH_FOLDER=\"${GRAPH_FOLDER}\"")
message(STATUS "In aby3-GORAM, GRAPH_FOLDER=${GRAPH_FOLDER}")