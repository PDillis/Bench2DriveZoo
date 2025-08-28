## Follow these steps to install the environment
- **STEP 1: Create environment**
    ```
    ## python3.8 should be strictly followed.
    conda create -n b2d_zoo python=3.9
    conda activate b2d_zoo
    ```
- **STEP 2: Install cudatoolkit**
    ```
    conda install -c "nvidia/label/cuda-12.9.0" cuda-toolkit
    ```
- **STEP 3: Install torch**
    ```
    pip install uv
    uv pip install torch torchvision --index-url https://download.pytorch.org/whl/cu129
    ```
- **STEP 4: Set environment variables**
    ```
    export PATH=/usr/bin/gcc:$PATH
    export CUDA_HOME=usr/local/cuda-12.9/
    ```
- **STEP 5: Install ninja and packaging**
    ```
    uv pip install ninja packaging
    ```
- **STEP 6: Install our repo**
    ```
    uv pip install -r requirements.txt
    ```
- **STEP 7: Install CARLA for closed-loop evaluation.**

    ```
    ## Ignore the line about downloading and extracting CARLA if you have already done so.
    mkdir carla
    cd carla
    wget https://carla-releases.s3.us-east-005.backblazeb2.com/Linux/CARLA_0.9.15.tar.gz
    tar -xvf CARLA_0.9.15.tar.gz
    cd Import && wget https://carla-releases.s3.us-east-005.backblazeb2.com/Linux/AdditionalMaps_0.9.15.tar.gz
    cd .. && bash ImportAssets.sh
    export CARLA_ROOT=YOUR_CARLA_PATH

    ## Important!!! Otherwise, the python environment can not find carla package
    uv pip install carla==0.9.15
    ```
