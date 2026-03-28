# Installation

## System Requirements

The following minimum system requirements are recommended to run EmbodiChain reliably. These are the tested configurations during development — other Linux distributions and versions may work but are not officially supported.

- Operating System: 
    - Linux (x86_64): Ubuntu 20.04+

- NVIDIA GPU and drivers:
    - Hardware: NVIDIA GPU with compute capability 7.0 or higher
    - NVIDIA Driver: 535 or higher (recommended 570)


- Python:
    - 3.10
    - 3.11

Notes:

- Ensure your NVIDIA driver is compatible with your chosen PyTorch wheel.
- We recommend installing PyTorch from the official PyTorch instructions for your CUDA version: https://pytorch.org/get-started/locally/

---

### Recommended: Install with Docker 

We strongly recommend using our pre-configured Docker environment, which contains all necessary dependencies.

```bash
docker pull dexforce/embodichain:ubuntu22.04-cuda12.8
```

After pulling the Docker image, you can run a container with the provided [scripts](../../../docker/docker_run.sh).

```bash
./docker_run.sh [container_name] [data_path]
```

---


### Set Up a Virtual Environment

We strongly recommend using a virtual environment to avoid dependency conflicts. We recommend [uv](https://docs.astral.sh/uv/), a fast Python package manager, but conda also works.

**Option A: Using `uv` (Recommended)**

Install `uv`:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Create a virtual environment with Python 3.10 or 3.11:

```bash
uv venv --python 3.11
```

Activate the virtual environment:

```bash
source .venv/bin/activate
```

**Option B: Using `conda`**

```bash
conda create -n embodichain python=3.11
conda activate embodichain
```

### Install EmbodiChain

To install EmbodiChain from pypi, run:

```bash
pip install embodichain --extra-index-url http://pyp.open3dv.site:2345/simple/ --trusted-host pyp.open3dv.site

# Or install with the lerobot extras:
pip install embodichain[lerobot] --extra-index-url http://pyp.open3dv.site:2345/simple/ --trusted-host pyp.open3dv.site
```

To install the Embodichain from source, clone the EmbodiChain repository:
```bash
git clone https://github.com/DexForce/EmbodiChain.git
```

Install the project in development mode:

```bash
pip install -e . --extra-index-url http://pyp.open3dv.site:2345/simple/ --trusted-host pyp.open3dv.site

# Or install with the lerobot extras:
pip install -e .[lerobot] --extra-index-url http://pyp.open3dv.site:2345/simple/ --trusted-host pyp.open3dv.site
```

> [!NOTE]
> * [LeRobot](https://huggingface.co/docs/lerobot/installation) is an optional module for EmbodiChain that provides data saving and loading functionalities for robot learning tasks. Installing with the `lerobot` extras will include this module and its dependencies.

### Verify Installation
To verify that EmbodiChain is installed correctly, run a simple demo script to create a simulation scene:

```bash
python scripts/tutorials/sim/create_scene.py

# Or run in headless mode.
python scripts/tutorials/sim/create_scene.py --headless
```
---
