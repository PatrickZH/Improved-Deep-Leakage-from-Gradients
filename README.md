# Improved-Deep-Leakage-from-Gradients
The code for "[Improved Deep Leakage from Gradients](https://arxiv.org/pdf/2001.02610.pdf)" (iDLG).

## Abstract <br>
It is widely believed that sharing gradients will not leak private training data in distributed learning systems such as Collaborative Learning and Federated Learning, etc. Recently, Zhu et al. [1] presented an approach which shows the possibility to obtain private training data from the publicly shared gradients. In their Deep Leakage from Gradient (DLG) method, they synthesize the dummy data and corresponding labels with the supervision of shared gradients. However, DLG has difficulty in convergence and discovering the ground-truth labels consistently. In this paper, we find that sharing gradients definitely leaks the ground-truth labels. We propose a simple but reliable approach to extract accurate data from the gradients. Particularly, our approach can certainly extract the ground-truth labels as opposed to DLG, hence we name it Improved DLG (iDLG). Our approach is valid for any differentiable model trained with cross-entropy loss over one-hot labels. We mathematically illustrate how our method can extract ground-truth labels from the gradients and empirically demonstrate the advantages over DLG. <br><br>


## Experiments <br>
| Dataset | DLG | iDLG |
 :-: | :-: | :-:
| MNIST | 89.9% | 100.0% |
| CIFAR-100 | 83.3% | 100.0% |
| LFW | 79.1% | 100.0% |


Table 1: Accuracy of the extracted labels for DLG [1] and iDLG. Note that iDLG always extracts the correct
label as opposed to DLG which extracts wrong labels frequently.

<br><br>
<div align=center><img src="https://github.com/PatrickZH/Improved-Deep-Leakage-from-Gradients/blob/master/Figure1.png"/></div>


<br><br>
<div align=center><img src="https://github.com/PatrickZH/Improved-Deep-Leakage-from-Gradients/blob/master/Figure2.png"/></div>
<br><br>

## Cite <br>
```
@article{zhao2020idlg,
  title={iDLG: Improved Deep Leakage from Gradients},
  author={Zhao, Bo and Mopuri, Konda Reddy and Bilen, Hakan},
  journal={arXiv preprint arXiv:2001.02610},
  year={2020}
}
```


## Our further work <br>
We further leveraged gradient matching to condense the large training set - [Dataset Condensation with Gradient Matching](https://openreview.net/forum?id=mSAKhLYLSsl). <br>
Code can be found in [Code](https://github.com/VICO-UoE/DatasetCondensation). <br>
Our experiments show that we can condense large training sets into tiny synthetic ones and obtain good generalization ability when train arbitrary randomly initialized deep networks with them.  <br>
|  | MNIST | FashionMNIST | SVHN | CIFAR10 |
 :-: | :-: | :-: | :-: | :-:
| 1 img/cls  | 91.7 | 70.5 | 31.2 | 28.3 |
| 10 img/cls | 97.4 | 82.3 | 76.1 | 44.9 |
