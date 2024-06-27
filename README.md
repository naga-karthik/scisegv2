# SCIsegV2: A Universal Tool for Segmentation of Intramedullary Lesions in Spinal Cord Injury

This repository contains the official code for our MICCAI AMAI submission titled "SCIsegV2: A Universal Tool for Intramedullary Lesions in Spinal Cord Injury"

## Using SCIsegV2

### Install dependencies

1. Create a new virtual environment using conda or venv

```console
conda create -n scisegv2 python=3.9 -y
```
2. [Install nnUNet from its official repository](https://github.com/MIC-DKFZ/nnUNet/blob/master/documentation/installation_instructions.md#installation-instructions)

3. [Install Spinal Cord Toolbox](https://spinalcordtoolbox.com/user_section/installation.html)

4. Install the remaining dependencies 

```console
pip install -r requirements.txt
```

### Running the code

1. Given that our datasets were in [BIDS](https://bids-specification.readthedocs.io/en/stable/) format, we provide a script that converts BIDS-formatted datasets to the nnUNet format. The usage examples are provided in 
`dataset_conversion/convert_bids_to_nnUNetv2_all_sci_data.py`

2. Once nnUNet is installed, define the required variables in `training_scripts/run_scisegv2.sh` and run the following command:

```console
bash training_scripts/run_scisegv2.sh
```


### Computing the metrics

1. We use the open-source [MetricsReloaded](https://github.com/Project-MONAI/MetricsReloaded) package for the metrics. The installation instructions can be found [here](https://github.com/Project-MONAI/MetricsReloaded). 

2. Once installed, run the following command to compute the metrics:

```console

python testing/compute_metrics_reloaded.py \ 
    -prediction /path/to/predictions \
    -reference /path/to/labels \
    -metrics dsc nsd rel_vol_error \
    -output /path/to/output/metrics.csv

```

