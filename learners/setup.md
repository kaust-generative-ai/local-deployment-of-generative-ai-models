---
title: Setup
---

FIXME: Setup instructions live in this document. Please specify the tools and
the data sets the Learner needs to have installed.

## Data Sets

<!--
FIXME: place any data you want learners to use in `episodes/data` and then use
       a relative link ( [data zip file](data/lesson-data.zip) ) to provide a
       link to it, replacing the example.com link.
-->
Download the [data zip file](https://example.com/FIXME) and unzip it to your Desktop

## Install Miniforge, Conda, Mamba

If you haven't already done so, install [Miniforge](https://github.com/conda-forge/miniforge). Miniforge provides minimal installers for [Conda](https://conda.io/) and [Mamba](https://github.com/mamba-org/mamba) specific to [conda-forge](https://conda-forge.org/), with the following features pre-configured:

   * Packages in the base environment are obtained from the `conda-forge` channel.
   * The `conda-forge` channel is set as the default (and only) channel.

Conda/mamba will be the primary package managers used to install the required Python dependencies. For convenience, a script is included that will download and install Miniforge, Conda, and Mamba.

::: tab

### Linux

```bash
curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"
bash Miniforge3-$(uname)-$(uname -m).sh
```

### Mac

```bash
curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"
bash Miniforge3-$(uname)-$(uname -m).sh
```
### Windows

TODO

:::

## Software Setup

:::::::::::::::: spoiler

## LLaMA C++

The instructions below will walk you through the process of installing the software required for the episodes of this lesson that focus on LLaMA C++ using the environment configuration files and build scripts in the [kaust-generative-ai/local-deployment-llama-cpp](https://github.com/kaust-generative-ai/local-deployment-llama-cpp) repository on GitHub.

### Clone the Git Repository

```bash
git clone https://github.com/kaust-generative-ai/local-deployment-llama-cpp.git
cd local-deployment-llama-cpp/
```

### Create the Conda Environment

Creating the Conda environment for LLaMA C++ depends on your operating system, whether your CPU supports specific hardware acceleration, and whether you have access to a GPU. Create a Conda environment in a sub-directory `env/` of your project directory by running one of following shell scripts.

::: tab

### CPU Only (Linux, Mac, Windows)

```bash
./bin/create-conda-env.sh
```

### Metal GPU (Mac)

In order to support Metal GPU acceleration available on Macs with ARM CPUs you need to install a few extra dependecies. These dependencies are added to the  `environment-metal-gpu.yml` and `requirements-metal-gpu.txt` files.

```bash
./bin/create-conda-env.sh environment-metal-gpu.yml
```

### NVIDIA GPU (Linux, Windows)

In order to support NVIDIA GPU acceleration you need to install a few extra dependecies. These dependencies are added to the `environment-nvidia-gpu.yml` and `requirements-nvidia-gpu.txt` files.

```bash
./bin/create-conda-env.sh environment-nvidia-gpu.yml
```

:::

### Install LLaMA C++

TODO

### Build LLaMA C++ from Source (Optional)

TODO

::::::::::::::::::::::::

:::::::::::::::: spoiler

## Llamafile

The instructions below will walk you through the process of installing the software required for the episodes of this lesson that focus on Llamafile using the environment configuration files and build scripts in the [kaust-generative-ai/local-deployment-llamafile](https://github.com/kaust-generative-ai/local-deployment-llamafile) repository on GitHub.

### Clone the Git Repository

```bash
git clone https://github.com/kaust-generative-ai/local-deployment-llamafile.git
cd local-deployment-llamafile/
```

### Create the Conda Environment

TODO

### Install Llamafile

TODO

### Build Llamafile from Source (Optional)

TODO

::::::::::::::::::::::::

:::::::::::::::: spoiler

## Ollama

The instructions below will walk you through the process of installing the software required for the episodes of this lesson that focus on Ollama using the environment configuration files and build scripts in the [kaust-generative-ai/local-deployment-ollama](https://github.com/kaust-generative-ai/local-deployment-ollama) repository on GitHub.

### Clone the Git Repository

```bash
git clone https://github.com/kaust-generative-ai/local-deployment-ollama.git
cd local-deployment-ollama/
```

### Create the Conda Environment

TODO

### Install Ollama

TODO

::::::::::::::::::::::::
