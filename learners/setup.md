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

TODO

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
