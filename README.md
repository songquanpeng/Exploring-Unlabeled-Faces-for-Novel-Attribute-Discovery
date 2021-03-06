# Exploring Unlabeled Faces for Novel Attribute Discovery

***This is an ongoing unofficial implementation.***

**Current progress:**
+ [x] Generate the pseudo labels.
+ [x] Verify the cluster results.
+ [x] Modify the dataloader.
+ [x] Implement the attribute summary instance normalization (ASIN).
+ [x] Modify the generator.
+ [x] Modify the discriminator.
+ [x] Implement the latent loss.
+ [x] Generate fixed images per sample step.
+ [x] Implement the test function.
+ [ ] Qualitative evaluation on CelebA.
+ [ ] Facial attribute translation on CelebA.
+ [ ] Image Translation between multiple datasets.

## Dependencies
```shell script
pip install -r requirements.txt

# Install faiss (optional)
# CPU version only
conda install faiss-cpu -c pytorch

# GPU version
conda install faiss-gpu cudatoolkit=10.0 -c pytorch # For CUDA10

```

## Datasets
### CelebA
https://www.dropbox.com/s/d1kjpkqklf0uw77/celeba.zip

## Training & Testing
```sh
# Generate pseudo labels
python ./scripts/generate_labels.py --dataset_path D:\Research\Data\celeba\images \
                                    --batch_size 32

# Inspect pseudo labels
python ./scripts/inspect_labels.py

# Train with the CelebA dataset
./scripts/train.sh

# Resume training
./scripts/resume.sh 2021-03-02_16-55-25 10000

# Test with the CelebA dataset
./scripts/test.sh

# Use tensorboard:
tensorboard --logdir=./logs --bind_all
```


## Reference
1. The code is based on [StarGAN](https://github.com/yunjey/StarGAN).
2. https://arxiv.org/abs/1912.03085
3. https://github.com/wielandbrendel/bag-of-local-features-models