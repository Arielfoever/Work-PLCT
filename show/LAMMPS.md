# 用于演示的 LAMMPS

## 安装 openMPI

安装

## 构建 LAMMPS

下载源代码。见 [Build LAMMPS with make](https://docs.lammps.org/Build_make.html)

```
git clone https://github.com/lammps/lammps.git --depth=1
cd lammps
mkdir build
cd build   
make serial     # 构建单机程序
make mpi        # 构建mpi版本
```

构建完成后在 `lammps/src` 产生 `lmp_serial` `lmp_mpi`。

## 运行

### 单机版

```
lmp_serial -in ./in.airebo
```

### 联机版

需要准备 `hosts` 文件并确保相同机器的路径上均安装了相同的文件。

```
mpirun -machinefile hosts -n 6 lmp_mpi
```

## 查看结果

vmd 可用于查看生成的 `sample.xyz` 描述文件。
`res/img-*.ppm` 为图片。使用 `cat img-*.ppm | ffmpeg -y -f image2pipe -c:v ppm -i - -r 20 movie.avi` 可以将其拼接为视频。
