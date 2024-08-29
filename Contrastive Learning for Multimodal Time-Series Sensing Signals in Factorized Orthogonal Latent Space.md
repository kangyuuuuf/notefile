# Contrastive Learning for Multimodal Time-Series Sensing Signals in Factorized Orthogonal Latent Space

This note is based on the pape, [FOCAL: Contrastive Learning for Multimodal Time-Series Sensing Signals in Factorized Orthogonal Latent Space](https://arxiv.org/abs/2310.20071), for learning purpose. 

### Preface

The main goal of foundation model is to generate a compenhesive model that could cover the main latent fecture/space given one dataset. That is
$$
f (x) \rightarrow z
$$
where $z$ is the fectures and $x$ is the data sample. Theorically, once the foundation model has the capable to catch the features, it can be used to implement various application based on this model.

### Methodology

There are various methods to generate foundation model based on unlabel data. However, labelled data is always expensive since it requires the manpower to label the data. One of the solution is to use the **contrastive learning**, which is a self-supervised learning. Basically, the general idea is, with the given dataset, we set a based criteria to decide whether is positive pair (the sample that has strong relationship) or negative pair (the sample do not have the relation) and use the nerual network to train a model such that samples that are positive pair will generate similar output while that are negative pair will generate different feature space. Usually, we use **orthogonal loss** as loss function to train the model during the learning.

#### SimCLR



#### CMC





## Sever Usage

enter server: ssh tk_server

quit: exit/control d

tls- current session

tat [name] - enter session

quit control b -> d

tks [name] - remove session

tns [name] - create session

ns - check current chip

tls



**Run command**

```bash
python3 train.py -gpu=0 -model=TransformerV4 -learn_framework=InfoMAE -stage=pretrain -dataset=PAMAP2
```

**check current training chart**

return to the main tmux, 

tensorboard –logdir [weight folder dir]

## Using Density Model

In the density model, we are using density ratio loss to measure the performance of encoder during the pertrain.

![image-20240109215624460](Contrastive%20Learning%20for%20Multimodal%20Time-Series%20Sensing%20Signals%20in%20Factorized%20Orthogonal%20Latent%20Space.assets/image-20240109215624460.png)

#### Density Ratio Loss

For the density ratio loss, we can divide it into 2 parts, which are 
$$
\mathcal L = sharedLoss + privateLoss
$$
![image-20240109215831633](Contrastive%20Learning%20for%20Multimodal%20Time-Series%20Sensing%20Signals%20in%20Factorized%20Orthogonal%20Latent%20Space.assets/image-20240109215831633.png)

##### Shared Loss

**Remember, we only have one shared discriminator for given modality input, and one joint shared discriminator**



The shard loss measures the loss of shared fearture among all the modalities. It contains two terms: **Total Correlation**(TC) and Shared Mutual Info(I). 

By the tick of mathematics, we can approximate the TC and I by

<img src="Contrastive%20Learning%20for%20Multimodal%20Time-Series%20Sensing%20Signals%20in%20Factorized%20Orthogonal%20Latent%20Space.assets/image-20240109220204606.png" alt="image-20240109220204606" style="zoom:50%;" />

Then, for the shared loss, we have
$$
\sum_{j}^m \log(\frac{D_1}{1-D_1}) + \sum_k^m \log \frac{1-D_2}{D_2}
$$
Where $D_1 = D(X_1,\dots, X_m|W_{xj})$ and $D_2 = D(x_k, W_{x,j})$, which means $num(D_1) =1 , num(D_2) = m$

#### Private Loss

The number of discriminators is the number of modalities.

The private loss measures the loss of private features. It contains two terms: reconstrustion and private mutual loss.

**Reconstruction Term:** measure the ability of the encoder to catch the feature of inpute data

**PMI:** measure it is private loss(not sure).

