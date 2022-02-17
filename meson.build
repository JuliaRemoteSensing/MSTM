project('mstm', 'fortran', version:'4.0', meson_version: '>=0.53', license: 'MIT')

bin_dir = get_option('bindir')
with_mpi = get_option('with-mpi')
with_mpich = get_option('with-mpich')

if with_mpich
    dependency('mpich', required: true)
endif

if with_mpi
    dependency('mpi', language: 'fortran', required: true)
endif

add_project_arguments('-O2', language: 'fortran')
add_project_arguments('-fallow-argument-mismatch', language: 'fortran')

if with_mpi or with_mpich
    executable('mstm',
        files('code/mpidefs-parallel.f90', 'code/mstm-intrinsics.f90', 'code/mstm-v4.0.f90'),
        install: true,
        install_dir: bin_dir)
else
    executable('mstm',
        files('code/mpidefs-serial.f90', 'code/mstm-intrinsics.f90', 'code/mstm-v4.0.f90'),
        install: true,
        install_dir:bin_dir)
endif
