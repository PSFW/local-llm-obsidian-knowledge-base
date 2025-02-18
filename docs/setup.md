
# Setup

Setup a huggingface token, local obsidian api key

Setup a [User Access Token](https://huggingface.co/docs/hub/security-tokens#user-access-tokens)

Open wsl in current folder by running `wsl` in terminal

Run commands:
```
#/bin/bash
export DOCKER_IMAGE=intelanalytics/ipex-llm-serving-xpu:latest
export CONTAINER_NAME=ipex-llm-serving-xpu-container
sudo docker run -itd --privileged --net=host device=/dev/dri -v "/mnt/d/Repos/local-llm-obsidian-knowledge-base/.devcontainer/models:/llm/models" -e "no_proxy=localhost,127.0.0.1" --memory="32G" --name=ipex-llm-serving-xpu-container --shm-size="16g" intelanalytics/ipex-llm-serving-xpu:latest
```


sudo docker run -itd --privileged --net=host --device=/dev/dri -v /mnt/d/Repos/local-llm-obsidian-knowledge-base/models:/llm/models -e no_proxy=localhost,127.0.0.1 --memory="32G" --name=ipex-llm-serving-xpu-container --shm-size="16g" intelanalytics/ipex-llm-serving-xpu:latest


docker exec -it ipex-llm-serving-xpu-container /bin/bash

apt-get install git-lfs
git lfs install

git credential approve <<EOF
protocol=https
host=huggingface.co
username=hf_token
password=
EOF


git config --global lfs.pruneoffsetdays 0 && git lfs prune
//cd models && git clone https://huggingface.co/unsloth/DeepSeek-R1-GGUF

git-lfs clone https://huggingface.co/unsloth/DeepSeek-R1-GGUF

git clone --no-checkout --filter=blob:none https://huggingface.co/unsloth/DeepSeek-R1-GGUF.git
cd DeepSeek-R1-GGUF
git config --global --add safe.directory /llm/models/DeepSeek-R1-GGUF
git sparse-checkout init --cone && git sparse-checkout set DeepSeek-R1-UD-IQ2_XXS
git checkout main
git lfs pull

DeepSeek-R1-UD-IQ2_XXS


sudo apt install python3-pip
//pip install -U "huggingface_hub[cli]"
sudo apt install "python3-huggingface_hub[cli]"


pip install huggingface_hub

python3 -m pip install -U "huggingface_hub[cli]"



sudo apt install python3.12-venv
python3 -m venv .env
source .env/bin/activate
python3 -m pip install -U "huggingface_hub[cli]"

HF_TOKEN=""
HF_HUB_CACHE="/mnt/d/Repos/local-llm-obsidian-knowledge-base/cache"

huggingface-cli download unsloth/DeepSeek-R1-GGUF DeepSeek-R1-UD-IQ2_XXS/DeepSeek-R1-UD-IQ2_XXS-00001-of-00004.gguf

huggingface-cli download unsloth/DeepSeek-R1-GGUF config.



wget --header="Authorization: Bearer $HF_TOKEN" hf/file/download/url




cd ./.devcontainer && DOCKER_BUILDKIT=0 docker build . -f Dockerfile.vllm-openai-ipex --network=host --build-arg HF_TOKEN= 




docker run --rm -it <layer-id>

docker run --rm -it efc9ea532bb2 bash -il