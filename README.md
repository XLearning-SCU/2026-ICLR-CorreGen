# Robust Multi-view Clustering against Imperfect Information

This repository provides the official PyTorch implementation of our paper:

> Zhichao Huang, Haochen Zhou, Hao Wang, Xi Peng, Mouxing Yang,<br>
> *Robust Multi-view Clustering against Imperfect Information*, NeurIPS 2026. 👉 [[Paper]](https://openreview.net/forum?id=1FPjSicyVu) [[Conference Page]](https://nips.cc/virtual/2026/loc/sydney/poster/156004)

## Introduction

- Real-world multi-view data often suffer from **imperfect information**, where **Incomplete Views (IV)** and **Noisy Correspondences (NC)** coexist. Both challenges stem from imperfect cross-view counterpart information: the counterpart of an anchor instance may be unavailable or unreliable.
- We propose **Posterior-guided Latent Counterpart Inference (PLCI)**, a unified framework that models the desired cross-view counterpart as a latent variable. PLCI combines **instance-level reliability estimation** with **prototype-level semantic transport** to infer its posterior distribution, providing reliable counterpart targets for learning from both mismatched pairs and incomplete instances.
- Experiments on **six multi-view datasets** against **10 state-of-the-art methods** demonstrate the effectiveness of PLCI under imperfect information. PLCI can also be incorporated into existing multi-view clustering methods to improve their robustness.

![Overview of PLCI: instance-level reliability estimation, prototype-level semantic transport, and latent counterpart inference.](figures/framework.pdf)

## Requirements

Python 3.11 is recommended. The main dependencies include `PyTorch`, `NumPy`, `SciPy`, `scikit-learn`, `PyYAML`, and `munkres`. Package versions are specified in [requirements.txt](requirements.txt).

```bash
pip install -r requirements.txt
```

## Configuration

Dataset-specific hyperparameters and network architectures are provided as YAML files in [config](config). Configurations are available for **Scene15**, **LandUse21**, **Reuters**, **CCV**, and **HandWritten**.

Pass the configuration path through `--config_file`, for example, `--config_file config/Scene15.yaml`. Values defined in the YAML file **override command-line arguments**.

## Usage

Clone this repository and navigate to the project directory:

```bash
git clone https://github.com/XLearning-SCU/2026-NeurIPS-PLCI.git
cd 2026-NeurIPS-PLCI
```

After installing the dependencies, run the script for your dataset:

```bash
bash script/Scene15.sh
bash script/LandUse21.sh
```

Each script launches four experiments concurrently, with paired noise and missing rates of `0`, `0.2`, `0.5`, and `0.8`. Adjust `CUDA_VISIBLE_DEVICES` in the scripts to match your available GPUs; Scene15 uses GPU `0` and LandUse21 uses GPU `1` by default.

Training results and console logs are saved under `test-Mixture_Scene15/` or `test-Mixture_LandUse21/`, respectively.

## Citation

If you find this repository useful in your research, please consider citing:

```bibtex
@inproceedings{huang2026robust,
  title={Robust Multi-view Clustering against Imperfect Information},
  author={Huang, Zhichao and Zhou, Haochen and Wang, Hao and Peng, Xi and Yang, Mouxing},
  booktitle={Advances in Neural Information Processing Systems},
  year={2026},
}
```
