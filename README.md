<p align="center">
  <h1 align="center">Controllable Texture Tiling with Transformed RoPE-Enhanced Diffusion Models</h1>
  <p align="center">
    <a href="https://scholars.cityu.edu.hk/en/persons/jrhuang8/"><strong>Junrong HUANG</strong></a>
    ·
    <a href="https://scholars.cityu.edu.hk/en/persons/zzhang452/"><strong>Zhiyuan ZHANG</strong></a>
    ·
    <a href="."><strong>Rui TANG</strong></a>
    ·
    <a href="https://hongbofu.people.ust.hk/"><strong>Hongbo FU<strong></a>
    ·
    <a href="https://scholars.cityu.edu.hk/en/persons/jingliao/"><strong>Jing LIAO*</strong></a>
  </p>
        
  <p align="center">
  <a href="https://arxiv.org/abs/2606.22945">
    <img src="https://img.shields.io/badge/arXiv-paper-b31b1b?style=for-the-badge&logo=arxiv&logoColor=white" alt="arXiv" />
  </a>
  <a href="https://modelscope.cn/models/heika94/control-tile/">
    <img src="https://img.shields.io/badge/ModelScope-model-FFD21E?style=for-the-badge&logo=modelscope&logoColor=white" alt="modelscope">
  </a>
  </p>



  <h2 align="center"><a href="https://dl.acm.org/doi/10.1145/3799902.3811172">SIGGRAPH 2026 (Conference)</a></h2>
  <div align="center">
    <img src="assets/teaser.jpg", width="80%">
  </div>
</p>


This repository contains the code for the paper Controllable Texture Tiling with Transformed RoPE-Enhanced Diffusion Models , accepted as a conference paper in SIGGRAPH 2026.

## Setup
The code is written in python 3.10 and uses PyTorch along with pytorch-lightning for distributed training.
Please create a new conda environment with python 3.10 and run the `setup.sh` script to install all the dependencies.

```bash
conda create -n ctile python=3.10
conda activate ctile

sh setup.sh
```

## Dataset & Pretrained Models

Our dataset can be downloaded [here](https://modelscope.cn/datasets/heika94/ctile-dataset) and be stored in `dataset` folder.

We also uploaded the baseline dataset [here](https://modelscope.cn/datasets/heika94/ctile-baseline), you can also store it in `dataset` folder.

The pretrained [models](https://modelscope.cn/models/heika94/control-tile/summary) can be downloaded [here](https://modelscope.cn/models/heika94/control-tile/resolve/master/model-lora.ckpt) and stored in `ckpt` folder.

After running the setup script and placing the dataset and checkpoints in the correct location, the directory structure should look like this:

```
    .
    |-- ControlTile <-- this repository
    |   |-- dataset
    |   |   |-- ctile-dataset
    |   |   |   |-- metadata
    |   |   |   |-- render
    |   |   |   |-- texture
    |   |   |
    |   |   |-- ctile-baseline
    |   |       |-- metadata
    |   |       |-- raw
    |   |       |-- synthesis
    |   |       |-- texture
    |
    |   |-- ckpt
    |       |-- model-lora.ckpt
    |   |-- output
    |       |-- logs
    |       |-- ckpt
    |   |-- ALL OTHER CONTENTS OF THIS REPOSITORY
```

## Training

```bash
# train with blender dataset
python run.py train_phase1
# train with adaptation dataset, remember to resume from phase1
python run.py train_phase2
```

## Testing

```bash
python run.py test
```

## Acknowledgements

We would like to express our sincere gratitude to **Manycore Tech Inc.** for providing the high-quality, photo-realistic datasets via [Spatial-Verse](https://spatial-verse.com/) that supported this research and development.

## Citation

```bibtex
@misc{huang2026controllabletexturetilingtransformed,
    title={Controllable Texture Tiling with Transformed RoPE-Enhanced Diffusion Models}, 
    author={Junrong Huang and Zhiyuan Zhang and Rui Tang and Hongbo Fu and Jnig Liao},
    year={2026},
    eprint={2606.22945},
    archivePrefix={arXiv},
    primaryClass={cs.GR},
    url={https://arxiv.org/abs/2606.22945}, 
}

@inproceedings{10.1145/3799902.3811172,
    author = {Huang, Junrong and Zhang, Zhiyuan and Tang, Rui and Fu, Hongbo and Liao, Jing},
    title = {Controllable Texture Tiling via Diffusion Transformers with Transformed Rotary Embeddings},
    year = {2026},
    isbn = {9798400725548},
    publisher = {Association for Computing Machinery},
    address = {New York, NY, USA},
    url = {https://doi.org/10.1145/3799902.3811172},
    doi = {10.1145/3799902.3811172},
    booktitle = {Proceedings of the Special Interest Group on Computer Graphics and Interactive Techniques Conference Conference Papers},
    articleno = {77},
    numpages = {11},
    keywords = {Texture Tiling, Diffusion Transformers, Image Inpainting, Generative Image Editing, Reference-guided Generation},
    series = {SIGGRAPH Conference Papers '26}
}
```


