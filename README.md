# Dynamic_Tanh
Experiments on Dynamic Tanh(Paper: Transformers without Normalization)

# Paper
- Link: https://arxiv.org/pdf/2503.10622
- Paper Review: https://haeun161.tistory.com/31

- This paper got the idea from the fact that LayerNorm in Transformer architecture showed a s-shape form which resembles scaled Tanh
  - ![image](https://github.com/user-attachments/assets/c6fa230e-1610-4b6a-a154-d253263bffc3)

# Experiment 1: Reconstruction Experiment on 'What do Normalization Layer do?'
1. **Reconstruction Experiment**: checked the input&output of LayerNorm in ViT
  - ![image](https://github.com/user-attachments/assets/c6fa230e-1610-4b6a-a154-d253263bffc3)
2. **Comparsion Test** : Checked the input & output of BatchNorm to see whether it has the same Pattern

## Results
- **ViT: LayerNorm**
  - ![image](https://github.com/user-attachments/assets/80c4aa36-b137-4d36-bbad-5e950fb1e187)
- **ResNet50: BatchNorm**
  - ![image](https://github.com/user-attachments/assets/48eada40-4baf-400a-8569-aead640c6386)


# Experiment 2: Reconstruction Experiment on Training with DyT in ResNet50(BatchNorm)
- According to the paper, Limation of DyT was that DyT struggled to fully replace BatchNormalization
  - ![image](https://github.com/user-attachments/assets/e8a6ca66-b715-4d06-96dc-8bf72aa5474d)

- Experiment Environment
  - Uses Pretrained ResNet50
    - with BatchNorm
    - Replace BatchNorm to DyT
  - Data: https://huggingface.co/datasets/timm/mini-imagenet
 
  ## Results
  - **BatchNorm**
    - ![image](https://github.com/user-attachments/assets/116ce909-6607-4dbd-8210-b9510af1ce55)
  - **DyT**
    - ![image](https://github.com/user-attachments/assets/ced9c5e5-67bc-464e-94a7-c266fb1824ab)
    - Learnable Param: alpha
      - ![image](https://github.com/user-attachments/assets/2bf71505-abac-42e8-a552-553398fa499a)


