cmake_minimum_required(VERSION 3.10)

project(MSTM VERSION 4.0.0 LANGUAGES Fortran)

option(ENABLE_MPI "Enable MPI parallelization" OFF)

if(ENABLE_MPI)
    find_package(MPI REQUIRED)
    set(CMAKE_FORTRAN_FLAGS "${CMAKE_FORTRAN_FLAGS} ${MPI_FORTRAN_FLAGS}")
    set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} ${MPI_EXE_LINKER_FLAGS}")

    add_executable(mstm code/mpidefs-parallel.f90 code/mstm-intrinsics.f90 code/mstm-v4.0.f90)
    include_directories(${MPI_INCLUDE_PATH})
    target_link_libraries(mstm MPI::MPI_Fortran)
    target_include_directories(mstm PRIVATE ${MPI_FORTRAN_INCLUDE_PATH})
else()
    add_executable(mstm code/mpidefs-serial.f90 code/mstm-intrinsics.f90 code/mstm-v4.0.f90)
endif(ENABLE_MPI)
