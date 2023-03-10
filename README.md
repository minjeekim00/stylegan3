## Alias-Free Generative Adversarial Networks (StyleGAN3) <br>
#### Official code is [here](https://github.com/NVlabs/stylegan3)

## Full FFHQ dataset
#### Download [FFHQ dataset](https://drive.google.com/drive/folders/1tZUcXDBeOibC6jcMCtgRRz67pzrAHeHL) for full size dataset.

## Getting started
**Git**
Clone this repository by running this:
```.bash
git clone https://github.com/minjeekim00/stylegan3.git
```

Change your current directory to stylegan3 code
```.bash
cd stylegan3
```


**Docker**: You can run the above curated image example using Docker as follows:
```.bash
# Run Docker container:
docker run --gpus all -it --rm --user $(id -u):$(id -g) -v `pwd`:/workspace --workdir /workspace -e HOME=/workspace  m40030811/stylegan3 bash
```

## Quality metrics

```.bash
python calc_metrics.py --metrics=fid50k_full --data=./datasets/ffhq-1024x1024.zip --mirror=1 \
    --network=https://api.ngc.nvidia.com/v2/models/nvidia/research/stylegan3/versions/1/files/stylegan3-t-ffhq-1024x1024.pkl
```

## Generate images
```.bash
# Generate an image using pre-trained FFHQ model (1024 x 1024 resolution).
python gen_images.py --outdir=out2 --trunc=1 --seeds=0-99 \
    --network=https://api.ngc.nvidia.com/v2/models/nvidia/research/stylegan3/versions/1/files/stylegan3-r-ffhq-1024x1024.pkl
```


Recommended metrics:
* `fid50k_full`: Fr&eacute;chet inception distance<sup>[1]</sup> against the full dataset.
* `kid50k_full`: Kernel inception distance<sup>[2]</sup> against the full dataset.
* `pr50k3_full`: Precision and recall<sup>[3]</sup> againt the full dataset.
* `ppl2_wend`: Perceptual path length<sup>[4]</sup> in W, endpoints, full image.
* `eqt50k_int`: Equivariance<sup>[5]</sup> w.r.t. integer translation (EQ-T).
* `eqt50k_frac`: Equivariance w.r.t. fractional translation (EQ-T<sub>frac</sub>).
* `eqr50k`: Equivariance w.r.t. rotation (EQ-R).

Legacy metrics:
* `fid50k`: Fr&eacute;chet inception distance against 50k real images.
* `kid50k`: Kernel inception distance against 50k real images.
* `pr50k3`: Precision and recall against 50k real images.
* `is50k`: Inception score<sup>[6]</sup> for CIFAR-10.

