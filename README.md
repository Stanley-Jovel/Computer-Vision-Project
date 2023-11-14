# TODO
- Files in test with sounds similar to gunshots

# Get Started
1. Create a virtual environment

`python3 -m venv venv`

2. Activate the virtual environment

`source venv/bin/activate`

3. Install the requirements

`pip install -r requirements.txt`

# insert_gunshots_into_backgrounds.ipynb

This notebook is used to insert gunshots into background sounds. 

First the background sounds are loaded from the `BACKGROUND_FOLDER`. Then each background is split into 10 second segments (or windows).

For each window, a gunshot from `GUNSHOT_FOLDER` is inserted at a random position. A given window has one gunshot from three different volume variations: `10%`, `50%` and `100%` volume.

Gunshot sounds are always picked at random (for now at least. We may want to change this later).

The output sounds are saved in `{OUTPUT_FOLDER}/audio`. Spectrograms are saved in `{OUTPUT_FOLDER}/spectrograms`.

Output filenames are of the form: 

`{backgroundName}_window={index}_vol={volumeLevel}_gun={gunshotName | 'none'}.wav`

Examples:

```
park_window=7_vol=10%_gun=Deset-Eagle.mp3
crowd_window=1_vol=50%_gun=none.mp3
constructionSite_window=3_vol=100%_gun=M249_6.mp3
```