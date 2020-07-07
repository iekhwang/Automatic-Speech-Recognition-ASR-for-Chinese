# ESPnet Setup

Clone the ESPnet repository.

```bash
git clone https://github.com/espnet/espnet.git
```

Create the Docker image from the local Dockefile, in our case we used CUDA Version 10.0, there is also a 10.1 alternative

```bash
cd espnet/docker/
./build.sh local 10.0
```

Run the ESPnet docker container from  Docker image

```bash
nvidia-docker run -it -v $(pwd)/espnet:/espnet espnet/espnet:gpu-cuda10.0-cudnn7-u18-local  /bin/bash
```

To get ESPnet to run, you will have to set some environment variables and build the project.

```bash
# docker file system
export CUDA_HOME=/usr/local/cuda-10.0
export CUDA_TOOLKIT_ROOT_DIR=$CUDA_HOME
export LD_LIBRARY_PATH="$CUDA_HOME/extras/CUPTI/lib64:$LD_LIBRARY_PATH"
export LIBRARY_PATH=$CUDA_HOME/lib64:$LIBRARY_PATH
export LD_LIBRARY_PATH=$CUDA_HOME/lib64:$LD_LIBRARY_PATH
export CFLAGS="-I$CUDA_HOME/include $CFLAGS"

cd /espnet/tools
make
```

This will take a wile. Get a coffee, do some laundry, write some papers.
To check if everything is working fine, navigate to the _an4_ example and run it.

```bash
cd /espnet/egs/an4/asr1
./run.sh --backend pytorch
```

**For Mandarin model Aishell-1**

```bash
cd espnet/egs/aishell/asr1
#set run.sh stage to -1
./run.sh --backend pytorch
```
_/espnet/egs_ has three Mandarin pre-build examples(Aishell-1, Aishell-2, aidatatang), you can modify the inner code and run your datasets.
