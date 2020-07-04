Mozilla DeepSpeech v0.6.0-alpha.4
=====



Git the v0.6.0-alpha.4 version from DeepSpeech
-----


```
git clone https://github.com/mozilla/DeepSpeech.git
```
```
cd DeepSpeech/
less VERSION
```

If the version is not v0.6.0-alpha.4, hard reset the version to v0.6.0-alpha.4

```
git reset --hard v0.6.0-alpha.4
```

Create a docker image and container on your server or laptop
-----

Create docker image
```
docker build -t mozilla_deepspeech:v6a4 .
```
Create and run docker container
```
nvidia-docker run -it -v $path/DeepSpeech:/DeepSpeech mozilla_deepspeech:v6a4 /bin/bash
```
Train your language model
-----

Please check the offical steps -> https://github.com/mozilla/DeepSpeech/tree/master/data/lm

You could also use [Baidu's language model](https://github.com/PaddlePaddle/DeepSpeech#language-model-released)

Train your model
-----

Please check a tiny model for training -> https://github.com/mozilla/DeepSpeech/blob/master/bin/run-ldc93s1.sh , you can also change the hyperparameters to your own.

The format of the input csv file is like:
```
wav_filename,wav_filesize,transcript
/DeepSpeech/data/ldc93s1/LDC93S1.wav,93638,she had your dark suit in greasy wash water all year
```

If you have problem with hyperparameters, you can check with ```python DeepSpeech.py --helpfull```

---------

If you have any problems with DeepSpeech v0.6.0-alpha.4, please do not hesitate to contact me iekhwang@outlook.com .
