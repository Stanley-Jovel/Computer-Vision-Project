# Get Started
1. Create a virtual environment

`python3 -m venv venv`

2. Activate the virtual environment

`source venv/bin/activate`

3. Install the requirements

`pip install -r requirements.txt`

# Generate Spectrograms
The notebook `Generate_Spectrograms.ipynb` is used to insert gunshots into background sounds.

First the background sounds are loaded from `/repo_dir/input/background`. Then each background is split into 10 second segments (or windows).

For each window, a gunshot from `/repo_dir/input/gushot` is inserted at a random position. A given window has one gunshot from three different volume variations: `8%`, `35%` and `70%` volume. There is a 20% chance that a window will have a non-gunshot inserted instead of a gunshot.

Gunshot (or non-gunshot) sounds are always picked at random.

The output spectrograms are saved in `/repo_dir/output/spectrograms`.

Classification labels are stored in `/repo_dir/output/labels.csv`, which is a CSV file with the following columns: 
`file_name,label`.
We can load this file using a custom `torch.utils.data.Dataset` class, and use it to create a dataloader for training.

Output filenames are of the form: 

`{backgroundName}_window={index}_vol={volumeLevel}_gun={0|1}.png`

Examples:

```
park_window=7_vol=10%_gun=1.png
crowd_window=1_vol=50%_gun=0.png
```

# Train Models
The notebook `Train_Models.ipynb` is used to train models.
`Double_Head_EffNetV2_Training.ipynb` has the dual headed Effnet model and training scripts.
