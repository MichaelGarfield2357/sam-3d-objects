# Build on Ubuntu 24.04.3 w/ RTX 5090

> Last updated @ Nov 21, 2025

### The following procedure is verified multiple times.

## Version
| Package | Repository | Version/Commit |
|---------|-----------|----------------|
| sam-3d-objects | [facebookresearch/sam-3d-objects](https://github.com/facebookresearch/sam-3d-objects.git) | 0e3d254f70c388efd10d6deae3f12a1344eb1957 |
| pytorch3d | [facebookresearch/pytorch3d](https://github.com/facebookresearch/pytorch3d) | V0.7.8 |
| kaolin | [NVIDIAGameWorks/kaolin](https://github.com/NVIDIAGameWorks/kaolin.git) | v0.18.0 |

- Clone them first and be aware of the **submodules**. 

## Build

- Download [sam3d-objects-single.yml](https://github.com/user-attachments/files/23684700/sam3d-objects-single.yml)

```
# Create environment
conda create -n sam3d-objects python=3.11

conda activate sam3d-objects

# Install torch
pip install torch==2.8.0 torchvision==0.23.0 torchaudio==2.8.0 --index-url https://download.pytorch.org/whl/cu128

# Update dependency
conda env update -f sam3d-objects-single.yml

# Refresh (This is necessary.)
conda deactivate
conda activate sam3d-objects

# Build pytorch3d
python setup.py install

# Build kaolin
pip install -e . --no-build-isolation

# Run demo.py
python demo.py

## GOOD LUCK ^_^
```

## Full Dependencies

- Please refer to the `sam3d-objects.yml` and `requirements.txt`

- [sam3d-objects.yml](https://github.com/user-attachments/files/23684670/sam3d-objects.yml)
- [requirements.txt](https://github.com/user-attachments/files/23684669/requirements.txt)


> These two files are generated using my pypi package [conda-env-export](https://pypi.org/project/conda-env-export/) via command `conda-env-export --pip-all --conda-all --separate`.
