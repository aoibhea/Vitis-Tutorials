3.3 Setting up board environment & Demo run
-----------------------
Before we get our hands on the board, there are some dependencies that need to be prepared in advance. In the previous module_1, user has downloaded the board environment with DPU hardware integrated. In this module, We need to add some runtime level software dependencies.
* The corresponding script is provided in the Module_3 repository. Copy the prerequisite files and compiled project to the evaluation board.
    ```
    $cd [DOWNLOAD_PATH]/Board_Dependency
    $./get_dependency_zcu104.sh
    $cp [SDK_INSTALLATION_PATH]/glog-0.4.0/build_for_petalinux/glog-0.4.0-Linux.tar.gz .
    $cd ..
    $scp -r Board_Dependency root@[IP_OF_BOARD]:~/
    $scp -r ~/Vitis-AI/Vitis-AI-Library/overview root@[IP_OF_BOARD]:~/
    $ssh root@[IP_OF_THE_BOARD]
    ```
 * Now we can operate on the board through an ethernet connection.
   * Install the Vitis AI related dependencies
   ```
   root@xilinx-zcu104-2019_2:~# cd Board_Dependency
   root@xilinx-zcu104-2019_2:~/Board_Dependency# ./install_dependency_zcu104.sh
   ```
   * Run the demo
   ```
   root@xilinx-zcu104-2019_2:~/Board_Dependency# cd ../overview/samples/refinedet
   root@xilinx-zcu104-2019_2:~/overview/samples/refinedet# ./test_performance_refinedet refinedet_pruned_0_96 test_performance_refinedet.list
   ```
   <p align="left">
   <img src="images/demo_single_thread.png">
   </p>
   Note that the user could also use parameters to define the number of threads and running time as below. For more detailed instruction, please refer to the Readme file within the refinedet folder.

   ```
   root@xilinx-zcu104-2019_2:~/overview/samples/refinedet# ./test_performance_refinedet refinedet_pruned_0_96 test_performance_refinedet.list -t 8 -s 60
   -t: <num_of_threads>
   -s: <num_of_seconds>
   ```
   <p align="left">
   <img src="images/demo_multi_threads.png">
   </p>

   Please follow the instruction on [Module 4](/Machine_Learning/Getting_Started/03-Basic/Module_4) for next step.

<p align="center"><sup>Copyright&copy; 2020 Xilinx</sup></p>
