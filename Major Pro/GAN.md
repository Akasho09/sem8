## A Generative Adversarial Network (GAN) 
- is a type of artificial intelligence model used to create new data that looks similar to real data (like images, audio, or text).

### 🧠 How GAN Works
- GAN has two main parts:
1. 1️⃣ Generator
- Creates fake data (like fake images).
- Tries to make data look real.

2. 2️⃣ Discriminator
- Checks whether the data is real or fake.
- Acts like a judge.
    - 👉 The generator tries to fool the discriminator.
    - 👉 The discriminator tries to catch the generator.
- This competition helps both networks improve over time.

### Used for:
- Image enhancement
- Denoising
- Super-resolution
- Image modality conversion
- Image registration

### 🔹 GAN Problems
- Traditional GANs suffer from:
    - Training instability
    - Mode collapse
    - Vanishing gradients

### ⭐ WGAN-GP (Key Concept)
- Improvement over traditional GANs.
    - ✔ Uses Wasserstein distance
    - ✔ Adds Gradient Penalty
    - ✔ Provides:
        - Stable training
        - Better image quality
        - More realistic outputs
