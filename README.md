# Visualizing the Curse of Dimensionality

 A simple visual experiment showing how **cosine similarity behaves as dimensionality increases**.

 The goal is to build an intuition for one of the geometric phenomena associated with the **curse of dimensionality**.

 ## The Experiment

 We generate pairs of independent random Gaussian vectors and calculate their cosine similarity while increasing the number of dimensions.

 The experiment uses:

 - **500 random vector pairs** per dimension
- Dimensions ranging from **2 to 7,000**
- Cosine similarity as the similarity measure
- A histogram to visualize the distribution of similarities

 The animation shows how the distribution changes as dimensionality increases.

 ## What happens?

 At low dimensions, cosine similarities are relatively spread out.

 As dimensionality increases, the distribution becomes increasingly concentrated around **0**.

 In other words:

 > Independent random vectors tend to become increasingly orthogonal as dimensionality increases.

 This can be seen in the animation as the distribution progressively concentrates around zero.

 ## Why is this related to the Curse of Dimensionality?

 The **curse of dimensionality** refers to a broader set of problems that arise when working with high-dimensional spaces.

 One important phenomenon is that the geometry of high-dimensional spaces behaves very differently from our intuition in 2D or 3D.

 For independent random vectors:

 $$
\cos(A,B) =
\frac{A \cdot B}{\|A\|\|B\|}
$$

 and as the dimensionality $d$ increases:

 $$
\cos(A,B) \rightarrow 0
$$

 The vectors become increasingly close to orthogonal.

 This experiment therefore illustrates one aspect of high-dimensional geometry associated with the curse of dimensionality.

 ### Important distinction

 This experiment does **not** mean that all high-dimensional vectors become similar to zero.

 The vectors in this experiment are **independent random vectors**.

 Real-world embeddings are different. Learned embeddings contain structure, meaning that semantically related vectors can still have high cosine similarity even when they contain hundreds or thousands of dimensions.

 The key takeaway is:

 > **High dimensionality changes the geometry of the space in ways that are often unintuitive from a low-dimensional perspective.**


 ## Running the Experiment

 ### Install dependencies

```
pip install numpy plotly kaleido imageio imageio-ffmpeg
```

 ### Run

```
python cosine_similarity.py
```

 The script generates:

```
visualize curse of dim.ipynb
```

 ## Method

 For each dimension $d$:

 1. Generate 500 pairs of independent Gaussian vectors.
2. Calculate the cosine similarity for every pair.
3. Compute the mean and standard deviation.
4. Plot the distribution.
5. Add the result to the animation.

 The vectors are generated using:

```
a = np.random.randn(n_trials, d)
b = np.random.randn(n_trials, d)
```

 Cosine similarity is calculated as:

```
similarity = np.sum(a * b, axis=1) / (
    np.linalg.norm(a, axis=1) *
    np.linalg.norm(b, axis=1)
)
```

 ## Technologies

 - Python
- NumPy
- Plotly
- ImageIO
- FFmpeg

 ## Key Takeaway

 The experiment provides a simple visual intuition for high-dimensional geometry:

 > **As dimensionality increases, independent random vectors tend to become nearly orthogonal, and their cosine similarities become increasingly concentrated around zero.**

 This is not the complete definition of the curse of dimensionality, but it is a useful way to visualize how dramatically geometry can change in high-dimensional spaces.

 ## License

 MIT License
