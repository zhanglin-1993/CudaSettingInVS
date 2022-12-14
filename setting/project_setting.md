0. 想要使用cuda编程，首先需要将当前工程设置为cuda工程：  
  右击工程-build dependencies-build customizations-使用的cuda版本（比如cuda11.1）  
1. 设置该工程的通用属性：  
  右击工程-properties-general，输出文件名，输出文件类型，输出文件路径，中间文件路径，SDK版本等  
2. 当建立一个工程后，会自动加载该工程所需要的通用文件：  
  右击工程-properties-VC++ directories-include directories/library directories.  
3. 想要调用非默认自动加载的库，以使用其中的函数借口，需要额外加入该头文件所在路径：  
  右击工程-properties-C/C++-general-additional include directories  
4. 在release版本下进行调试，需要关闭优化，否则变量的值或者调用顺序可能不是按照逻辑顺序进行的：  
  右击工程-properties-C/C++-optimization-optimization-disabled(/Od)  
5. 设置当前工程为cuda工程后，工程属性中会有cuda c/c++这一项，需要设置正确的cuda计算能力：  
  右击工程-properties-cuda C/C++-device-code generation-compute_60, sm_60. 比如使用RTX3060，从nvidia官网找到对应的计算能力为8.6  
(网址为https://developer.nvidia.com/cuda-gpus#compute)，则设置为compute_86, sm_86，代码中只需要#include "cuda_runtime.h"和#include "device_launch_parameters.h"即可.  
6. 设置额外的链接库路径以进行代码链接：  
  右击工程-properties-linker-general-additional include directories-C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.1\lib\x64  
7. 在额外的链接库路径中加入具体的库文件：  
  比如cudnn.lib, cufft.lib文件等  
8. 产生调试信息：  
   右击工程-properties-linker-debugging-generate debug info-generate debug information(/DEBUG)  
9. 想要进入cu文件以进行调试：  
  右击cu文件-properties-cuda c/c++-host-generate host debug information-yes(-g)  
10. 除了创建文件是选择cuda文件，也需要在文件属性确认是否为cuda文件：  
  右击cu文件-properties-cuda c/c++-general-item type-cuda c/c++  
![cuda_project_setting](https://github.com/zhanglin-1993/cudaApplication/blob/main/setting/cuda_project_setting.jpg "cuda_project_setting")
![cuda_file_setting](https://github.com/zhanglin-1993/cudaApplication/blob/main/setting/cuda_file_setting.jpg "cuda_project_setting")
![cuda_build_customization](https://github.com/zhanglin-1993/cudaApplication/blob/main/setting/cuda_build_customization.jpg "cuda_project_setting")
