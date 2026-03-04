# Uncover Underlying Correspondence for Robust Multi-view Clustering

This repository provides the official implementation of our paper:

> Haochen Zhou, Guofeng Ding, Mouxing Yang, Peng Hu, Yijie Lin, Xi Peng,  
> *Uncover Underlying Correspondence for Robust Multi-view Clustering*, ICLR 2026 (Oral).  👉 [[Paper]](https://openreview.net/forum?id=a4S1nQay3b)

## Introduction

- Given that real-world multi-view data widely suffer from the **Noisy Correspondence (NC)** problem, this work explores a novel path for multi-view learning. 
- Unlike existing methods that rely heavily on pre-defined (and potentially noisy) cross-view pairs, we assume the underlying correspondences are **unknown a priori** and reformulate multi-view learning as a **maximum likelihood estimation problem over the underlying cross-view correspondences**. This objective is elegantly solved via our EM-based algorithm, **CorreGen**. Through **CorreGen**, the model alternately uncovers the latent soft correspondence distributions and robustly optimizes the representation learning network. 
- **CorreGen** not only theoretically unifies and generalizes the classic InfoNCE loss but also achieves SOTA performance across various complex noise scenarios, providing a fresh perspective for robust multi-view learning.

![framework](/figures/framework.png)

## Requirements

This repository depends on the following core libraries: `PyTorch`, `NumPy`, `scikit-learn`,  `SciPy`, `munkres`. Recommended package versions are specified in `requirements.txt`.  You can install them by running:

```bash
pip install -r requirements.txt
```

## Configuration

The hyperparameters and training options for the four datasets used in the paper are provided as YAML configuration files in the `/config` directory.



## Datasets

The `/dataset` directory provides the Scene15 and LandUse21 datasets. All datasets used in this project can be downloaded from Google Drive:  [Google Drive](https://drive.google.com/drive/folders/1hDmvUXrEhMfx5l7vaUurtwj-4MhNhqdY?usp=sharing).



## Usage

After cloning this repository, navigate to the project directory and run:

```bash
python main_train.py --config_file Scene15.yaml
```

By default, the Mismatch Ratio (MR) and Corruption Ratio (CR) are set to 0.
You can specify different values via command-line arguments, for example:

```bash
python main_train.py --config_file Scene15.yaml --m_ratio 0.2 --c_ratio 0.2
```

Note that arguments defined in `--config_file` will override other command-line arguments.

The training results are recorded in `output/{training dataset}/log_train.txt`.



## Citation

If you find this repository useful in your research, please consider citing:

```bibtex
@inproceedings{zhou2026uncover,
  title={Uncover Underlying Correspondence for Robust Multi-view Clustering},
  author={Zhou, Haochen and Ding, Guofeng and Yang, Mouxing and Hu, Peng and Lin, Yijie and Peng, Xi},
  booktitle={The Fourteenth International Conference on Learning Representations},
  year={2026}
}
```



## Acknowledgement

This implementation is based on [DIVIDE](https://github.com/XLearning-SCU/2024-AAAI-DIVIDE).





