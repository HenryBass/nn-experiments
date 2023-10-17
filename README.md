# nn-experiments

Dump for experiments I do with neural networks

# 1D embedding
What does it look like when an autoencoder compresses data beyond it's minimal dimension? For example, purely random 2D points compressed to 1D.
The network has to represent two dimensions in one, which can be visualized in two ways:

1) Iterate over the latent dimension, plotting the extracted 2D position
   
![image](https://github.com/HenryBass/nn-experiments/assets/63601449/b4333c59-a35d-4aeb-9af8-97af3ae77549)

2) Iterating over 2D positions, coloring them according to their 1D embedded position

![image](https://github.com/HenryBass/nn-experiments/assets/63601449/09746217-6789-4607-bd0e-e36b2b9d2392)


(These visualizations are in the code, in the above order)

The first visualization, I feel, gives more insight into the problem. The network is essentially trying to create a space filling curve, such that every point in 2D is close to a point on the line. With a large enough model, and enough time, you'd expect to see this curve becoming increasingly dense, approacing a fractal dimension
of 2. For example, a Hilbert curve.

Insights:

1) It's cool that it's even possible for a network to represent fundimentally higher dimensional information in a lower dimentsion, as long as the encoder and decoder are complex enough.
2) This can provide intuition for higher dimensional cases. When an autoencoder compesses m dimensions into n, where n is significantly less than m, it's essentially doing high-dimensional origami, trying to fold a manifold to fill the a higher dimensional volume. In an extreme case, like bringing mnist down to 2 dimensions, the model is streaching and folding a sheet of rubber into a vast phase space. Like crumpled paper, this sheet can seemingly fill a volume despite being fundimentally lower dimensional.
