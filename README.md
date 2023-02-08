# Cross-lingual Deepfake Detection

This repository provides a partial implementation of the paper: Transferring Audio Deepfake Detection Capability across Languages (accepted by TheWebConf 2023). Other parts of the code are being sorted out and will be released soon.

## The Architecture of Cross-lingual Domain Adaptation System

We trained our detection network with four types of protocols, including two classic transfer-learning methods and three DA methods:
1. Finetune. Based on a source model pre-trained with all English data, we finetune it with the Chinese training data.
2. Naive model. Both Chinese and English data are fed into the backbone network in each batch without special training techniques.
3. Adversarial Domain Adaptation (ADA). We combine the backbone network with a discriminator and perform adversarial training on the feature extractor and discriminator.
4. Multiple kernel MMD (MK-MMD). The model learns language-invariant detection information by minimizing the source and target domain distribution discrepancy.
5. Joint MMD (JMMD). Similar to the MK-MMD model, the JMMD model aligns domains by minimizing the JMMD loss.

![The Architecture of Cross-lingual Domain Adaptation System](/figure/system.png)

## Dataset

This work is conducted on the DECRO dataset, which can be found [here](https://github.com/petrichorwq/DECRO-dataset). Deepfake cross-lingual evaluation dataset (DECRO) is constructed to evaluate the influence of language differences on deepfake detection.

## Reference

[1] [Rawnet2](https://github.com/asvspoof-challenge/2021)
```bibtex
@INPROCEEDINGS{tak2021rawnet2,
  author={Tak, Hemlata and Patino, Jose and Todisco, Massimiliano and Nautsch, Andreas and Evans, Nicholas and Larcher, Anthony},
  booktitle={ICASSP 2021 - 2021 IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP)}, 
  title={End-to-End anti-spoofing with RawNet2}, 
  year={2021},
  volume={},
  number={},
  pages={6369-6373},
  doi={10.1109/ICASSP39728.2021.9414234}}
```

[2] Jiang, Junguang, et al. "Transferability in deep learning: A survey." arXiv preprint arXiv:2201.05867 (2022).
```bibtex
@misc{jiang2022transferability,
      title={Transferability in Deep Learning: A Survey}, 
      author={Junguang Jiang and Yang Shu and Jianmin Wang and Mingsheng Long},
      year={2022},
      eprint={2201.05867},
      archivePrefix={arXiv},
      primaryClass={cs.LG}
}

@misc{tllib,
    author = {Junguang Jiang, Baixu Chen, Bo Fu, Mingsheng Long},
    title = {Transfer-Learning-library},
    year = {2020},
    publisher = {GitHub},
    journal = {GitHub repository},
    howpublished = {\url{https://github.com/thuml/Transfer-Learning-Library}},
}
```