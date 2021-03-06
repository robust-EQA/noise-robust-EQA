# Noise-robust-EQA

Code for the paper

[Noise Robust Embodied Question Answering Using Hierarchical Joint Learning]()

Setup
-----

Download the [SUNCG](https://github.com/facebookresearch/House3D/blob/master/INSTRUCTION.md#usage-instructions) dataset, [House3D](https://github.com/abhshkdz/House3D/tree/master/renderer#rendering-code-of-house3d) virtual environment and install [EmbodiedQA](https://github.com/facebookresearch/EmbodiedQA/blob/master/README.md) framework.

Replace all files in the training folder into the project of EmboiedQA.

Robust-VQA
----

For low-level noisy environments (20\% of noisy labels):

        python train_vqa_noise.py -input_type ques,image -identifier ques-image -noise_rate 0.2 -forget_rate 0.2 -exponent 1 -log -cache

For extremely noisy environments (45\% of noisy labels):

        python train_vqa_noise.py -input_type ques,image -identifier ques-image -noise_rate 0.45 -forget_rate 0.45 -exponent 1 -log -cache -log -cache

Robust-Navigation
----

For low-level noisy environments (20\% of noisy labels):

        python train_nav_noise.py -model_type lstm -identifier lstm -noise_rate 0.2 -forget_rate 0.2 -exponent 1 -log

For extremely noisy environments (45\% of noisy labels):

        python train_nav_noise.py -model_type lstm -identifier lstm -noise_rate 0.45 -forget_rate 0.45 -exponent 1 -log

Joint-Robust learning
---

        python train_eqa.py -nav_checkpoint_path /path/to/nav/ques-image-pacman/checkpoint.pt \
        -ans_checkpoint_path /path/to/vqa/ques-image/checkpoint.pt -identifier ques-image-eqa -log


