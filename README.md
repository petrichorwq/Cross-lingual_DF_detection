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