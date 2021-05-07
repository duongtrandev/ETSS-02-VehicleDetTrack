### Automation Lab, Sungkyunkwan University
# 2021 AI CITY CHALLENGE - TRACK 1

#### A Region-and-Trajectory Movement Matching for Multiple Turn-counts at Road Intersection on Edge Device ([The 5th AI City Challenge Track 1 - CVPR 2021](https://www.aicitychallenge.org/2021-challenge-tracks/))



---
### A. Evaluation on Nvidia Jetson Xavier NX

### Download the whole framework [HERE](https://o365skku-my.sharepoint.com/:u:/g/personal/duongtran_o365_skku_edu/EVqRPiGVYX5HukS0EVnDPw0BzuAWnr67Vo3p-dPeuxoTvg?e=SPreAg).


#### I. Video Data Import

Add video files to **/data/aicity2021_final_trt/video**.
   

The program folder structure should be as following:

```
AIC2021_Track1_SKKU_Automation_Lab
├── data
│   ├── aicity2021_final_trt
│   │   ├── video
│   │   │   ├── cam_1.mp4
│   │   │   ├── cam_1_dawn.mp4
│   │   │   ...
│   │   │   └── cam_20.mp4
...
```

#### II. Environment Setup

1. Hardware requirement:
* **SWAP size needs increase to 12GB before running**.

2. Install required libraries:

* OpenBlas: 
   ```shell  
   $ sudo apt-get install libopenblas-dev
   ```
* MAGMA: 
   * Download [MAGMA library](https://o365skku-my.sharepoint.com/:u:/g/personal/duongtran_o365_skku_edu/EZh8ORGHhwRNp6d1zzTcRUUBZJkl48K4jXBL_ZeqJ0uf-g?e=WYrawP).
   * Extract **magma** folder to **/usr/local** (root permission required).
      * The folder structure should be as below:
         ```
         usr
         ├── local
         │   ├── magma
         │   │   ├── include
         │   │   └── lib
         ...
        ```
   * Add MAGMA to your shared library path by appending to **.bashrc**:
      * ```shell
         export LD_LIBRARY_PATH=/usr/local/magma/lib:${LD_LIBRARY_PATH}
        ```
   * Finally, reload all libraries in Terminal with:
      * ```shell
         source ~/.bashrc
        ```   

3. Download preconfigured [virtualenv environment](https://o365skku-my.sharepoint.com/:u:/g/personal/duongtran_o365_skku_edu/EdIjzexL9Q9Kiy_fZecUyu8BrW-cC1Q66E31vIP6QqbCwA?e=H5gBfV) and extract **aic2021venv** folder.


4. Activate environment in Terminal with:

    ```shell
    $ source /path/to/aic2021venv/bin/activate
    ```

5. Build **.engine** TensorRT models in folder "**AIC2021_Track1_SKKU_Automation_Lab**" (*[more details](https://github.com/wang-xinyu/tensorrtx/tree/master/yolov5#how-to-run-yolov5s-as-example)*):

    ```shell
    $ bash bin/run_convert_yolov5s6.sh
    ```

#### III. Inference and Result Upload

1. Inference using TensorRT version of YOLOv5s6 in folder "**AIC2021_Track1_SKKU_Automation_Lab**" with:

    ```shell
    $ bash bin/run_inference_trt.sh
    ```

The final result will be in **data/aicity2021_final_trt/track1.txt**.

