# Mask-Guided-Cycle-GAN-for-Specular-Highlight-Removal

We convert the highlight removal problem to image-to-image translation by using cycle-consistent adversarial network (Cycle-GAN). The network can remove the specular highlight from natural images.
![](https://github.com/hootoon/Mask-Guided-Cycle-GAN-for-Specular-Highlight-Removal/blob/main/image/network.png)


We use a highlight mask estimated via the incorporation of the NMF method to guide the network.
![](https://github.com/hootoon/Mask-Guided-Cycle-GAN-for-Specular-Highlight-Removal/blob/main/image/NMF.png)


Several examples of our result can be seen as follows.
![](https://github.com/hootoon/Mask-Guided-Cycle-GAN-for-Specular-Highlight-Removal/blob/main/image/result.png)


## Dependencies

- python 3.7+
- pytorch 1.1+ & tochvision (cu102+)
- scikit-image

## Dataset

- [SHIQ](https://github.com/fu123456/SHIQ)

  ```
  @InProceedings{fu-2021-multi-task,
  author = {Fu, Gang and Zhang, Qing and Zhu, Lei and Li, Ping and Xiao, Chunxia},
  title = {A Multi-Task Network for Joint Specular Highlight Detection and Removal},
  booktitle = {Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)},
  year = {2021},
  pages = {7752-7761},
  month = {June},
  tags = {CVPR},
  }
  ```
  You can download the data from Google Drive. The link is: https://drive.google.com/file/d/1RFiNpziz8X5qYPVJPl8Y3nRbfbWVoDCC/view?usp=sharing (~1G).

- [LIME](https://vcai.mpi-inf.mpg.de/projects/LIME/)
  ```
  @inproceedings{meka2018lime,
  title={Lime: Live intrinsic material estimation},
  author={Meka, Abhimitra and Maximov, Maxim and Zollhoefer, Michael and Chatterjee, Avishek and Seidel, 
  Hans-Peter and Richardt, Christian and Theobalt, Christian},
  booktitle={Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition},
  pages={6315--6324},
  year={2018}
  }
  ```
  The download link is: https://download.mpi-inf.mpg.de/projects/LIME/LIME_TrainingData.rar

## Network

train

1. set the paths of the dataset in `train_l.py`, in line 44   `opt.dataroot = 'SHIQ_data'`. The `SHIQ_data` is the file path of the dataset.
2. run `train_l.py`
3. set the paths of the saved models achieved from step 2 `(netG_A2B.pth,netG_B2A.pth)`, in line54 ` netG_A2B = Generator_H2F.from_file('model/netG_A2B.pth')` and the dataset in `train.py`, which is similar to `train_l.py`.
4. run `train.py`

test

1. set the paths of the saved models achieved from step 4 `(netG_A2B.pth)` and the test dataset in `test.py`
2. run `test.py`

## Article
The article link is： https://www.sciencedirect.com/science/article/abs/pii/S0167865522002082
