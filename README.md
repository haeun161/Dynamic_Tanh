# Dynamic_Tanh
Experiments on Dynamic Tanh(Paper: Transformers without Normalization)

# Paper
- Link: https://arxiv.org/pdf/2503.10622
- Paper Review: https://haeun161.tistory.com/31

- This paper got the idea from the fact that LayerNorm in Transformer architecture showed a s-shape form which resembles scaled Tanh
  - ![image](https://github.com/user-attachments/assets/c6fa230e-1610-4b6a-a154-d253263bffc3)

# Experiment 1: Reconstruction Experiment on 'What do Normalization Layer do?'
1. **Reconstruction Experiment**: checks input&output of LayerNorm in ViT
2. **Comparsion Test** : Checks input & output of BatchNorm in ResNet50 to see whether it has the same Pattern(S-shaped)

## Results
- **ViT: LayerNorm**
  - ![image](https://github.com/user-attachments/assets/80c4aa36-b137-4d36-bbad-5e950fb1e187)
- **ResNet50: BatchNorm**
  - ![image](https://github.com/user-attachments/assets/7de461a7-fd31-4552-ae7c-ff5dfe5b4e10)



# Experiment 2: Reconstruction Experiment on Training with DyT in ResNet50(BatchNorm)
- According to the paper, Limation of DyT was that DyT struggled to fully replace BatchNormalization
  - ![image](https://github.com/user-attachments/assets/e8a6ca66-b715-4d06-96dc-8bf72aa5474d)
    
- **Experiment Environment**
  - torchvision 사용
    - torchvision.transforms
    - torchvision.models
  - Model: ResNet50
    - with BatchNorm
    - with DyT
  - Data: Mini version of Imagenet1K
    - https://huggingface.co/datasets/timm/mini-imagenet
  - Initialization of α:
    - Paper uses α=0.5 => however it didn't work well on ResNet50-DyT
    - In this experiment, I initialized α as 1.0(α=1.0)
    
  
## 2-1: Using Pretrained ResNet50
    
### Results
- **BatchNorm**
  - ![image](https://github.com/user-attachments/assets/116ce909-6607-4dbd-8210-b9510af1ce55)
- **DyT**
  - ![image](https://github.com/user-attachments/assets/ced9c5e5-67bc-464e-94a7-c266fb1824ab)
  - Learnable Param: alpha
    - ![image](https://github.com/user-attachments/assets/2bf71505-abac-42e8-a552-553398fa499a)

## 2-1: Using untrained ResNet50
 - due to the limitation of available GPU, it is trained till epoch 30.

### Results
- **BatchNorm**
  - ![image](https://github.com/user-attachments/assets/d84b40a5-2c7e-45ba-b6f8-b8e48403e463)

- **DyT**
  - ![image](https://github.com/user-attachments/assets/7ce761d3-d812-4f15-af95-74544caee483)
  - Learnable Param: alpha
    - ![image](https://github.com/user-attachments/assets/ea588dde-506c-4f59-b54f-0349336fb1be)


