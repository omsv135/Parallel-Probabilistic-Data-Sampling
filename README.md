# Parallel-Probabilistic-Data-Sampling Algorithms
Implementing MPI-based parallel data sampling methods based on the following paper: [https://ieeexplore.ieee.org/document/9130956](url)

The steps to run the project parallelly are as follows:
Step 1: Download the zip file from the GitHub repository in your working directory.
Step 2: Open the terminal/Powershell in your system and run ```ssh 172.27.19._``` where _ is any number from 1 to 60 (generally it is ``` ssh <to-the-computing-node>```.
Step 3: Upload files in the remote workspace through the command ```sftp``` (Simple File Transfer Protocol)
Step 4: Create a text file and name it as hostfile.txt. It contains the IP addresses of the computing nodes.
Step 5: Now the following command in the terminal:
```
mpirun -np 8 --hostfile hostfile.txt python3 gbs.py -b 16 -r $samp -o Isabel_gbs_$samp Isabel_Pressure_Large.vti
```
mpirun is the command which uses MPI to run the code in parallel. It has the following options:
```
Options:
  -np                   shows the processes we are going to run
  -hostfile.txt         file containing IP addresses of the computing nodes
```
Options in Algorithms we implemented:

```
  -h, --help            show this help message and exit
  -r FLOAT, --sampling-ratio=FLOAT
                        sampling ratio between 0 and 1 [default: 0.001]
  -o FILE_NAME, --out-file=FILE_NAME
                        name of output vtp file [default: out_srs.vtp]
  -v, --verbose         detailed log
  -t, --track-time      Append to srs_time.csv in format: proc_num,reading_tim
                        e,scatter_time,comp_time,gather_time,saving_time,total
                        _time
  -b                    Nuber of bins (only for value-based sampling and gradient-based sampling)
  -r                    Sampling Ratio
```

Miscellaneous

We made two shell scripts for 
