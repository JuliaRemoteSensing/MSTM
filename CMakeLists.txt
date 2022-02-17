cmake_minimum_required(VERSION 3.10)

project(MSTM VERSION 4.0.0 LANGUAGES Fortran)

find_package(MPI REQUIRED)

add_executable(mstm code/mpidefs-parallel.f90 code/mstm-intrinsics.f90 code/mstm-v4.0.f90)

target_link_libraries(mstm MPI::MPI_Fortran)

target_include_directories(mstm PRIVATE ${MPI_FORTRAN_INCLUDE_PATH}) 
