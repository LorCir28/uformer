# NN project: Schiavella (1884561), Cirillo (1895955)

# Uformer
### _A General U-Shaped Transformer for Image Restoration_


This notebook presents the architecture and application of the Uformer neural network. It consists of a Transformer-based encoder-decoder structure. The innovations introduced in this architecture are:

- A nonoverlapping window-based self-attention instead of global self-attention
- A learnable multi-scale restoration modulator in the form of a multi-scale spatial bias to adjust features in multiple layers
 

The Uformer network is used for the application purpose of image restoration. In particular, it is applied to two specific tasks:

- Denoising: image noise removal
- Deblurring: removal of image blurring

Our project will focus on the first task, denoising, which in Uformer's paper is performed on the two benchmarks: the Smartphone Image Denoising Dataset (SIDD) and the Darmstadt Noise Dataset (DND).

The evaluation measures on which the performance of the denoising process is evaluated are the structural similarity index measure (SSIM) and the peak signal-to-noise ratio (PSNR).

In conclusion, our project aims to repurpose the working Uformer architecture for the denoising task, without constraints on achieving the same evaluation metrics as the state-of-the-art.

![Uformer Architecture](./img/architecture.png "Uformer Architecture")

# General structure

The project repository is organized as follows:
- _code_: contains the _Uformer_ notebook and functional folders
	- _mod, no_mod_: directories in which the results of the project are. The latter are already present about the train and the experiments carried out by us. Consequently, tests can be run with these files, without having to train the network again.

**ATTENTION: Running a complete network train will overwrite files already present in _mod_ and _no_mod_**.

- _datasets_: groups the various versions of the SSID_ dataset.
    - _Full_SSID_dataset_: the most complete version of the dataset
    - _SSID_dataset_: the lightest version of the dataset
    - _Try_SSID_dataset_: contains only a few samples for testing the views of the dataset samples

**ATTENTION: The above dataset directories do NOT contain all the samples for the actual dataset. This is so that the user can more easily download the repository and test the entire notebook. Aware of this, the user must keep in mind that the results may not be good without the full/light dataset.**

- _img_: some significant images of the Uformer architecture

- _papers_: some important articles for the project

Considering all these files, the project has a size of almost **3 GB**.

# Full test preliminaries

All packages needed for the project are automatically installed when the notebook is started.

Downloading the full/light dataset is the most important step to fully test the project. To do this, just follow the following steps:

- Download the SSID dataset from [SSID_dataset](https://www.eecs.yorku.ca/~kamel/sidd/), following the instructions on the site. The downloaded directory should contain 3 items:
     - A _Data_ directory containing the samples.
     - Two text files _ReadMe_sRGB_ and _Scene_Instances_.

- Place all three elements in the repository folder related to the downloaded dataset type. It is recommended that you delete all files in these folders before making the transition

- Open the _Uformer_ notepad, go to the _Global_ section and perform:
    - If you downloaded the **full_dataset**: Change _use_full_dataset_ to **True**
    - If you downloaded the **lightweight dataset**: Change _use_full_dataset_ to **False**

By performing this procedure, you can run the tests with a suitable dataset. The project will weigh **12GB** if you downloaded the full dataset, or **6GB** with the lightweight one.

# Run test

All the necessary elements, other than the dataset and paths, are already present in the notebook.

Testing the program is very easy: it is required to run sequentially all the cells of the notebook. 
The only errors that may occur are relative to wrong/misspelled paths.

Errors similar to the latter can occur in the _Test_ section, when loading pretrained models. To solve them, simply add ".zip" to the path name in the notebook cell.

With Windows operating systems, the _num_worker_ parameter related to Pytorch dataloaders may cause some problems. To avoid this, set this value to 0.

The first cell of the _Global_ section, the one relating to the connection to Google Drive, must only be executed if the notebook is run on Google Colab.
 
**ATTENTION: There may be some problems displaying mathematical formulas when opening the notebook on GitLab. Therefore, it is recommended to download the repository**
