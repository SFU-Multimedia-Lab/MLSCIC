# MLSCID


Multi-Task Learning for Screen Content Image Coding Dataset and Pre-trained Models

The following instructions talk about dataset and pre-trained models, which are explained in the paper titled "Multi-Task Learning for Screen Content Image Coding."

> "Multi-Task Learning for Screen Content Image Coding."<br />
> Rashid Zamanshoar Heris, Ivan Bajic <br />
> https://arxiv.org/----------





## Installation

***Note: First, you need to instal the TensorFlow Compression (TFC) library. Details on how to instal TensorFlow Compression can be found at the following link.
https://github.com/tensorflow/compression
In summary, the necessary instructions for installation are given below.

### pip

To install TFC via `pip`, run the following command:

```bash
pip install tensorflow-compression
```

To test that the installation works correctly, you can run the unit tests with:

```bash
python -m tensorflow_compression.all_tests
```

Once the command finishes, you should see a message ```OK (skipped=29)``` or
similar in the last line.

## Usage
### Using a pre-trained model to compress an image
There are 4 pre-trained models with different lambda sizes, which can be downloaded from the below links:

bmshj2018_2Dec	"https://vault.sfu.ca/index.php/s/tPq7IMZVIo733wo/download"

bmshj2018_SC	"https://vault.sfu.ca/index.php/s/im6lQhLw5wNAg6n/download"

ms2020_2Dec		"https://vault.sfu.ca/index.php/s/uiTmjr2fix1O9jQ/download"

ms2020_SC		"https://vault.sfu.ca/index.php/s/BNJgxbMVtCkuYH5/download"



In the repository (https://github.com/SFU-Multimedia-Lab/MLSCID/Scripts), you'll find four Python scripts. For each model, you need to download the related script file and run:


```bash
python script.py <model> compress <input PNG file> <output TFCI file>
```
will compress an image using a pre-trained model and write a file ending in
`.tfci`. 


```bash
python script.py <model> decompress <input TFCI file> <output PNG file>
```

will decompress a TFCI file and write a PNG file. By default, an output file
will be named like the input file, only with the appropriate file extension
appended (any existing extensions will not be removed).


### As example:

1- Download a pre-trained model: 
```bash
wget -c https://vault.sfu.ca/index.php/s/tPq7IMZVIo733wo/download -O bmshj2018_2Dec.tar
tar xvf bmshj2018_2Dec.tar
```

2- Compress a PNG file (you can use the PNG files from the MLSCID-test.tar.gz)
```bash
python Scripts/bmshj2018-2Dec.py --model_path "bmshj2018_2Dec/lambda_0.01/bmshj2018/" compress MLSCID-test/SC_N_110.png TFCI-files/SC_N_110.png.tfci
```

3- Decompress a TFCI file
```bash
python Scripts/bmshj2018-2Dec.py --model_path "bmshj2018_2Dec/lambda_0.01/bmshj2018/" decompress TFCI-files/SC_N_110.png.tfci Reconstructed_Images/Rec_SC_N_110.png
```

## Training dataset

The training dataset contains 3000 images and their corresponding segmentation masks. You can download the training dataset from the following link:

MLSCID-training-sets "http://vault.sfu.ca/index.php/s/KMs4eQswIEHfbq7/download"



## Citation

If you use this datset for research purposes, please cite:
```
@paper{,
  author = "Rashid Zamanshoar Heris, Ivan Bajic",
  title = "Multi-Task Learning for Screen Content Image Coding",
  
}
