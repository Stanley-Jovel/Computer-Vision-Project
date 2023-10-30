# Get Started
1. Create a virtual environment

`python3 -m venv venv`

2. Activate the virtual environment

`source venv/bin/activate`

3. Install the requirements

`pip install -r requirements.txt`

4. Rename the file `.env.example` to `.env`. Replace the default values from the variables with the absolute paths to the folders where the audio files will be stored in your local set up. The folders you need to specify are: 
```
BACKGROUND_FOLDER = '/path/to/backgroundSounds'
GUNSHOT_FOLDER = '/path/to/gunshotSounds'
OUTPUT_FOLDER = '/path/to/outputSounds'
```

# insert_gunshots_into_backgrounds.ipynb

This notebook is used to insert gunshots into background sounds. 

First the background sounds are loaded from the `BACKGROUND_FOLDER`. Then each background is split into 10 second segments (or windows).

For each window, a gunshot from `GUNSHOT_FOLDER` is inserted at a random position. The same window has three different volume variations: `10%`, `50%` and `100%` volume.

Gunshot sounds are always picked at random (for now at least. We may want to change this later).

The output sounds are saved in `OUTPUT_FOLDER`.

Output filenames are of the form: 

`{backgroundName}_window={index}_gun={gunshotName}_vol={volumeLevel}.wav`

Examples:

```
park_window=7_gun=Deset-Eagle_vol=10%.mp3
crowd_window=1_gun=AK-12_vol=50%.mp3
constructionSite_window=3_gun=M249_6_vol=100%
```