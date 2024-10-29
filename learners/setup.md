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

## LLaMA C++, Llamafile, Ollama, and Friends

The exact software stack that you need to install depends on which episodes on the lesson that you plan to work through.

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

For convenience there is an installer script which can be used to download pre-compiled [LLaMA C++][LLaMA C++](https://github.com/ggerganov/llama.cpp) binaries for various OS, CPU, and GPU architectures and install the binaries into the `bin/` directory of the Conda environment. You can find the latest [release](https://github.com/ggerganov/llama.cpp/releases) for LLaMA C++ on GitHub and pass the link to the zip archive for your desired release to the script as a command line argument.

```bash
./bin/install-llama-cpp.sh "$RELEASE_URL"
```

For reference, here are a few examples.

::: tab

### Linux (Ubuntu, Intel CPU)

```bash
DOWNLOAD_URL=https://github.com/ggerganov/llama.cpp/releases/download/
TAG=b3868
RELEASE_ARCHIVE=llama-b3868-bin-ubuntu-x64.zip
RELEASE_URL="$DOWNLOAD_URL"/"$TAG"/"$RELEASE_ARCHIVE"
./bin/install-llama-cpp.sh "$RELEASE_URL"
```

### Mac (ARM CPU, Metal GPU)

```bash
DOWNLOAD_URL=https://github.com/ggerganov/llama.cpp/releases/download/
TAG=b3868
RELEASE_ARCHIVE=lllama-b3868-bin-macos-arm64.zip
RELEASE_URL="$DOWNLOAD_URL"/"$TAG"/"$RELEASE_ARCHIVE"
./bin/install-llama-cpp.sh "$RELEASE_URL"
```

### Mac (Intel CPU)

```bash
DOWNLOAD_URL=https://github.com/ggerganov/llama.cpp/releases/download/
TAG=b3868
RELEASE_ARCHIVE=llama-b3868-bin-macos-x64.zip
RELEASE_URL="$DOWNLOAD_URL"/"$TAG"/"$RELEASE_ARCHIVE"
./bin/install-llama-cpp.sh "$RELEASE_URL"
```

### Windows (Intel CPU)

```bash
DOWNLOAD_URL=https://github.com/ggerganov/llama.cpp/releases/download/
TAG=b3868
RELEASE_ARCHIVE=llama-b3868-bin-win-avx512-x64.zip
RELEASE_URL="$DOWNLOAD_URL"/"$TAG"/"$RELEASE_ARCHIVE"
./bin/install-llama-cpp.sh "$RELEASE_URL"
```

:::

### Build LLaMA C++ from Source (Optional)

If there isn't an official release available for your target operating system, then you will need to build LLaMA C++ from source. Don't worry, we have created build scripts to make this process as painless as possible. After creating the Conda environment using the instructions above you can build LLaMA C++ by running a command similar to the following to build LLaMA C++ from source within the activated Conda environment so that the build process has access to the required build tools compiler toolchain.

```bash
conda run --prefix ./env --live-stream ./bin/build-llama-cpp.sh
```

This command does the following.

1. Properly configures the Conda environment using the `conda run` command prior to running the `build-llama-cpp.sh` script.
2. Clones LLaMA C++ into `./src/llama-cpp`.
4. Builds LLaMA C++ with support for CPU acceleration using OpenBlas in `./build/llama-cpp`.
5. Installs the binaries into the `bin/` directory of the Conda environment.
6. Removes the `./src/llama-cpp` directory as it is no longer needed.
7. Removes the `./build/llama-cpp` directory as it is no longer needed.

Depending on what CPU and GPU hardware you have available, there are other build scripts that use different compiler flags to optimize LLaMA C++ binaries.

::: tab

### Mac (ARM CPU, Metal GPU)

#### Install XCode and Command Line Tools

If you are using Mac OS, then you will need to install [XCode](https://developer.apple.com/xcode/) and then run the following command to install XCode Command Line Tools in order to build from source.

```bash
xcode-select --install
```

#### Support for Metal GPU acceleration

After creating the Conda environment you can build LLaMA C++ by running the following command.

```bash
conda run --prefix ./env --live-stream ./bin/build-llama-cpp-metal-gpu.sh
```

### Linux (NVIDIA GPU)

After creating the Conda environment you can build LLaMA C++ by with support for GPU acceleration by running the following command.

```bash
conda run --prefix ./env --live-stream ./bin/build-llama-cpp-nvidia-gpu.sh
```

For a detailed discussion of additional NVIDIA GPU compilation options that might improve performance on particular GPU architectures see the [LLaMA C++ build documentation](https://github.com/ggerganov/llama.cpp/blob/master/docs/build.md#cuda).

:::

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
