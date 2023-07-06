# Vision Transformer

## About

Re-implementation of Vision Transformer

## TODO

- [x] Image Preprocessing
- [x] Patching
- [x] Flattening
- [x] Linear Projection
- [x] Position Embedding
- [x] CLS Token
- [x] Transformer
   - [x] Attention
   - [x] Feedforward
- [x] MLP Head Classifier

## Datasets

- [x] MNIST (98%)
- [x] CIFAR-10 (75.25%)
- [ ] Tiny ImageNet

## Model

### Arch

- Patch + Position Embedding (Extra learnable class embedding)
- Linear Projection of Flattened Patches
- Transformer Encoder
- MLP Head (Contains GeLU)
- Class (Bird, Ball, Car)

### Transformer Encoder

- Embedded Patches
- Norm (Layer Norm?)
- MHA
- Add (Identity + Activation)
- Norm (Layer Norm?)
- MLP
- Add (Identity + Activation)

## Image Handling

- Reshape image x { R(HxWxC) into eq of flattened 2d patches xp { R(N*(P**2 * C))
  where (H, W) is res, C is channel count, (P, P) is res of each image patch,
  N = HW / P**2 is resulting number of patches, also servces as effective input seq
  len for Transformer. Transformer uses constant latent vector size D through all layers,
  patches flattened to map to D dimensions with trainable linear projection, output of
  this projection are patch embeddings.