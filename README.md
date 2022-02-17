# MSTM 4.0

Hi!  Located here are the files for the multiple sphere T matrix fortran-90 code, D. W Mackowski et al.

You can build `MSTM` easily if you have [Meson](https://mesonbuild.com/index.html) installed:

```shell
meson build && cd build
meson install
```

Options:

- `with-mpi`: if this option is `true`, `MSTM` will be built in parallel mode. Meson will try to find the path of MPI
  and configure the compilation for you. Default is `false`.
- `with-mpich`: if this option is `true`, `MSTM` will be built in parallel mode. Meson will try to find the path of
  MPICH and configure the compilation for you. Default is `false`.
- `bindir`: set the installation target directory. Default is `bin`.

Example:

```shell
meson build -Dwith-mpi=true && cd build
meson install
```

If Meson cannot find the MPI/MPICH library, or if the compiler complains `Cannot open module file 'mpi.mod'`, you need
to set the environment variable `FC` while running `meson`:

```shell
FC=mpifort.mpich meson build -Dwith-mpich=true && cd build
meson install
```
