cmake_minimum_required( VERSION 2.8 )

project( ndanilov_rows_matrix_sum )

message( STATUS "-- " ${PROJECT_NAME} )
add_executable( ${PROJECT_NAME} main.cpp )

find_package( MPI REQUIRED )
if( MPI_FOUND )
    include_directories( ${MPI_INCLUDE_PATH} )
endif( MPI_FOUND )

if( MPI_COMPILE_FLAGS )
    set_target_properties( ${PROJECT_NAME} PROPERTIES COMPILE_FLAGS "${MPI_COMPILE_FLAGS}" )
endif( MPI_COMPILE_FLAGS )

if( MPI_LINK_FLAGS )
    set_target_properties( ${PROJECT_NAME} PROPERTIES LINK_FLAGS "${MPI_LINK_FLAGS}" )
endif( MPI_LINK_FLAGS )

target_link_libraries( ${PROJECT_NAME} ${MPI_LIBRARIES} )
