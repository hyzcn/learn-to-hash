
# Learning Space Partitions for Nearest Neighbor Search #

This is the code for our paper [**Learning Space Partitions for Nearest Neighbor Search**](https://arxiv.org/abs/1901.08544).
Yihe Dong, Piotr Indyk, Ilya Razenshteyn ilyaraz@microsoft.com , Tal Wagner.
_________________

The code is structured around a few centralized scripts, with additional versatile components that implement a common interface, which can be swapped to run different learning methods. This modular structure allows easy extensibility of our framework to new learning methods.

# Code layout #

[kahip/kmkahip.py](kahip/kmkahip.py): main backbone for creating knn graphs from dataset, recursively partitioning dataset using KaHIP in parallel, and learning tree of neural networks in tandem with building partitions tree.

[workflow_learn_kmeans](workflow_learn_kmeans.py): Main pipeline for running unsupervised learning methods: k-means, PCA, ITQ, random projection.

There are numerous additional scripts that provide utilities for training, model construction, partitioning, knn graph creation, data processing, etc.

# Demo #

For any given configuration as specified in utils.py, one can run any script with a __main__ function. We provide two demo scripts as simple examples:

[demo_km.py](demo_km.py): unsupervised learning, can use methods including k-means, PCA tree, ITQ, and random projection.

[demo_train.py](demo_train.py): supervised learning using KaHIP partitions, training can be either neural networks or logistic regression.

To change the various configurations, such as adjusting between different learning methods or datasets, one can either modify the corresponding options under the parse_args function, or pass them in through the command line.

# Prerequisites #

* PyTorch 0.4 or above.
* KaHIP
* scikit-learn (version insensitive)
* numpy (version insensitive)

# Directory configuration #

To point to the various resources needed at runtime, the file [config](config) in the base directory needs to contain the following absolute paths:

kahip_dir: directory to KaHIP installation.

data_dir: data directory, containing data such as knn graphs, and to contain various data produced at runtime.

glove_dir: directory containing GloVe partitions, specifically, subdirectories named "partition_256_strong" containing output of KaHIP in a file named "partition.txt".

sift_dir: directory containing SIFT partitions, analogous to above. E.g. subdirectories named "partition_16_strong" containing output of KaHIP in a file named "partition.txt".

