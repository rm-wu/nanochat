# How to install triton on B300


```shell
cd ~
git clone git checkout bfeb066872bc1e8b2d2bc0a3b295b99dd77206e7
cd ~/triton/

apt-get update && apt-get install -y zlib1g-dev libxml2-dev


# relevant triton git hash from here https://github.com/pytorch/pytorch/blob/v2.9.1/.ci/docker/ci_commit_pins/triton.txt
# it must match correctly the torch version
git checkout bfeb066872bc1e8b2d2bc0a3b295b99dd77206e7
uv venv
uv pip install -r python/requirements.txt
uv pip install -e . 

cd /your/repo
uv add ~/triton
export CUDA_HOME=/usr/local/cuda-13.0
export PATH="$CUDA_HOME/bin:$PATH"
export LD_LIBRARY_PATH="$CUDA_HOME/lib64:${LD_LIBRARY_PATH}"
export TRITON_PTXAS_PATH="$(which ptxas)"
```
