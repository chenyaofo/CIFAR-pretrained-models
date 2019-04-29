# CIFAR-pretrained-models

## Accuracy in the Validation Set

The validation is performed with the original view of the image(size=32x32).

**Note**: the FLOPs only counts the conv and linear layer.

| Model         | Acc@1(C10) | Acc@5(C10) | Acc@1(C100) | Acc@5(C100) | #param. | FLOPs |
|---------------|------------|------------|-------------|-------------|---------|-------|
| Resnet20[[1]] |            |            |             |             |         |       |
| Resnet32[[1]] |            |            |             |             |         |       |
| Resnet56[[1]] |            |            |             |             |         |       |
| PreactResnet20[[2]] |            |            |             |             |         |       |

## Pretrained Models

All the pretrained models are avaliable in the [release](https://github.com/chenyaofo/CIFAR-pretrained-models/releases).

## Implementation Details

The models are trained and exported with Pytorch(1.0.1.post2) and torchvision(0.2.1).

The training data augumentation follow [[1]],
```
torchvision.transforms.Compose([
    torchvision.transforms.RandomCrop(size=32, padding=4),
    torchvision.transforms.RandomHorizontalFlip(),
    torchvision.transforms.ToTensor(),
    torchvision.transforms.Normalize(
        mean=[0.49139968, 0.48215827, 0.44653124],
        std=[0.24703233, 0.24348505, 0.26158768],
    ),
])
```

All the models are trained with a mini batch size of 256 and the following optimizer,
```
torch.optim.SGD(..., lr=0.1, momentum=0.9, dampening=0, weight_decay=1e-4, nesterov=True)
```
the following scheduler,
```
torch.optim.lr_scheduler.MultiStepLR(..., milestones=[100,150], gamma=0.1)
```
the total training epochs is 200.


## Reference

1. He, Kaiming and Zhang, Xiangyu and Ren, Shaoqing and Sun, Jian. Deep residual learning for image recognition. In *CVPR*, 2016.

[1]: https://www.cv-foundation.org/openaccess/content_cvpr_2016/html/He_Deep_Residual_Learning_CVPR_2016_paper.html

2. Kaiming He, Xiangyu Zhang, Shaoqing Ren, Jian Sun. Identity Mappings in Deep Residual Networks. In *ECCV*, 2016.

[2]: https://link.springer.com/chapter/10.1007/978-3-319-46493-0_38

## Acknowledgement

Thanks for the computer vision community and github open source community.
