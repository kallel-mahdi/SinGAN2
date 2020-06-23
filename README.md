# pt-singan-single-image-gan

[WIP] Inofficial implementation of the paper __"[SinGAN: Learning a Generative Model from a Single Natural Image](https://arxiv.org/pdf/1905.01164.pdf)"__ as a project for the _Deep Generative Models_ lecture at TU Darmstadt SS2020.

<a href="https://github.com/jonasgrebe/pt-singan-single-image-gan/graphs/contributors">
  <img src="https://contributors-img.web.app/image?repo=jonasgrebe/pt-singan-single-image-gan" />
</a>

## Note
- Inner Steps in the Official Implementation?
- Spectral Normalization instead of Gradient Penalty? Other Loss Functions?
- Deformable Convolutions in Generator/Discriminator?


## How to use

For each of the exemplary SinGAN applications, we created an easy-to-use python script that can be run directly from the console by specifying the necessary parameters. All of these scripts have in common that they require either just the run_name of a pretrained SinGAN model or the --not_pretrained flag together with the number of scales N and the number of steps per scale. For instance, the following additional command line arguments would train a SinGAN model with 8 scales and 2000 steps per scale:

```console
python application.py [...] --not_pretrained --N 8 --steps_per_scale 2000
```

If the not_pretrained flag is not given but a trained model with the identifier run_name exists, this is used instead.

### Random Sampling

```console
python sample.py --run_name <String> --img 5026-green-fern-plant-during-daytime.jpg -- height <int> --width <int>
```

### Scale Injection

```console
python scale_injections.py --run_name <String> --img 5026-green-fern-plant-during-daytime.jpg
```

### Super Resolution

```console
python scale_injections.py --run_name <String> --img 5026-green-fern-plant-during-daytime.jpg --super_scales <int>
```

### Paint2Image
_Note_: You have to additionally provide a training image via --img if you want to train a new model. The paint images are expected to be found in the data/paint subdirectory.

```console
python paint2image.py --run_name <String> --paint 5026_1.jpg
```
### Single Image Animation

```console
python animate.py --run_name <String> --frames <int> --fps <int> --alpha 0.1 --beta 0.9 --start_at_scale <int>
```

## Example results

### Random Sampling

training (512x512)         |         512x512           |         512x512           |          512x512          |         512x1024
:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:
![train](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/data/5026-green-fern-plant-during-daytime.jpg) |![img1](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_5026/0_0.jpg) |![img2](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_5026/0_1.jpg) |![img3](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_5026/0_2.jpg) |![img4](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_5026/size_512x1024.jpg) 
![train](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/data/473-brown-rock-wall.jpg) |![img1](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_473/0_0.jpg) |![img2](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_473/0_1.jpg) |![img3](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_473/0_2.jpg) |![img4](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_473/size_512x1024.jpg) 
![train](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/data/1497-calm-body-of-water-near-tall-trees-during-daytime.jpg)  |![img1](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_1497/0_0.jpg) |![img2](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_1497/0_1.jpg) |![img3](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_1497/0_2.jpg) |![img4](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_1497/size_512x1024.jpg) 

----

### Scale Injections

training (512x512)         |         Scale 0/10           |         Scale 1/10           |          Scale 2/10          |         Scale 3/10   |         Scale 4/10
:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:
![train](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/data/5026-green-fern-plant-during-daytime.jpg) |![img1](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_5026/inj_0.jpg) |![img2](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_5026/inj_1.jpg) |![img3](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_5026/inj_2.jpg) |![img4](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_5026/inj_3.jpg) |![img5](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_5026/inj_4.jpg) 

Scale 5/10         |         Scale 6/10          |         Scale 7/10           |          Scale 8/10          |         Scale 9/10 |         Scale 10/10
:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:
![train](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_5026/inj_4.jpg) |![img6](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_5026/inj_5.jpg) |![img7](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_5026/inj_6.jpg) |![img8](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_5026/inj_7.jpg) |![img9](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_5026/inj_8.jpg) |![img10](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_5026/inj_9.jpg) |![img11](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_5026/inj_10.jpg)

training (512x512)         |         Scale 0/10           |         Scale 1/10          |          Scale 2/10          |         Scale 3/10   |         Scale 4
:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:
![train](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/data/473-brown-rock-wall.jpg) |![img1](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_473/inj_0.jpg) |![img2](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_473/inj_1.jpg) |![img3](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_473/inj_2.jpg) |![img4](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_473/inj_3.jpg) |![img5](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_473/inj_4.jpg) 

Scale 5/10         |         Scale 6/10          |         Scale 7/10           |          Scale 8/10          |         Scale 9/10 |         Scale 10/10
:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:
![train](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_473/inj_4.jpg) |![img6](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_473/inj_5.jpg) |![img7](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_473/inj_6.jpg) |![img8](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_473/inj_7.jpg) |![img9](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_473/inj_8.jpg) |![img10](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_473/inj_9.jpg) |![img11](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_473/inj_10.jpg)

### Super Resolution

training (512x512)         |       SinGAN  (1616x1616)     |         bilinear (1616x1616)          |  
:-------------------------:|:-------------------------:|:-------------------------:|
![train](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/data/5026-green-fern-plant-during-daytime.jpg) | ![img1](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_5026/img_sr_4r.jpg) | ![img2](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_5026/img_bilinear_4r.jpg)
![train](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/data/856-zebra-in-savanna.jpg) | ![img1](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_856/img_sr_4r.jpg) | ![img2](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_856/img_bilinear_4r.jpg)

----

### Paint2Image
training       |       paint   |   Scale 7/9   |    Scale 9/9
:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:|
![train](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/data/5026-green-fern-plant-during-daytime.jpg)  | ![img1](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/data/paint/5026_1.jpg)| ![img2](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_5026/paint_5026_1_7.jpg) | ![img3](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_5026/paint_5026_1_9.jpg)

training       |       paint   |   Scale 6/9   |    Scale 9/9
:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:|
![train](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/data/473-brown-rock-wall.jpg)  | ![img1](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/data/paint/473_1.jpg)| ![img2](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_473/paint_473_1_6.jpg) | ![img3](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_473/paint_473_1_9.jpg)
----

### Single Image Animation

training       |       animation   |
:-------------------------:|:-------------------------:|
![train](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/data/lightning.jpg) | ![img1](https://github.com/jonasgrebe/pt-singan-single-image-gan/blob/master/samples/singan_lightning/animation.gif)
