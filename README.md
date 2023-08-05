# TEGD_thirdai_hackathon
A neural DB based google drive search engine

## Installation

1. Wispher
```python
!git clone https://github.com/ggerganov/whisper.cpp.git  
%cd /content/whisper.cpp/models  
!bash download-ggml-model.sh base.en  
%cd ..  
!make   
```
2. ffmpeg (apt)
 

## Requirements
```python
pydub 
thirdai
thirdai[neural_db]
langchain
openai
paper-qa
requests
bs4
pandas



```
## Directory Structure

- book_web_Scrapping:
    > To Download the books from the web (NCERT)

- Thirdai_gdrive_engine_TEGD.ipynb
    > main script to run the search engine

    
## Usage

To run the search engine:
- Open the notebook with google colab
- mount the drive by executing the very first cell 
```python 
from google.colab import drive
drive.mount('/content/drive')
```

### NOTE:
> We are having a user input option in the notebook, as the extraction and training of audio file is time consuming.

> Please give input as `y` to the cell if you want to train your G-Drive's audio files.

```python
mp3_train = False
print("Do you want to fetch and train mp3 files too?")
print("It will take a lot of time. You can skip it for now")
if 'y' in input("Press 'y' to extract audio files else press 'n'").lower():
  mp3_train = True
```

By running the notebook `Thirdai_gdrive_engine_TEGD.ipynb` 

- The drive will be mounted to the notebook
- Get all the files in your G-Drive 

> Currently we are working on the `pdfs`, `docx`, `mp3` and `wav` files. The other file format like all `source code` file and `mp4` file will be added soon.

- For processing audio files
    - Download ggml-whisper which is a really fast version of whisper written in C/C++
    - Convert an audio file with any format to wav (the only format currently supported by ggml-whisper)
    - Convert the transcription to csv and save for model training later

- We are storing a map for each audio_csv file to its original localtion in the drive. So that when we query from the engine, we can redirect the output to original location.

- Get the `General_QnA` model from the  `bazaar`

- PREPARE INSERTABLE DOCS 
    - from pdfs
    - docx
    - mp3 (created earlier)

- SEARCH THE QUERY (from user input), and you will get the exact location of the file in the drive.

## DATA Link

https://drive.google.com/drive/folders/1tNJ-r6-URDAcU0VOZJ_h50hs4PrO5EkN?usp=sharing


## Try Our Demo

[DEMO](https://github.com/git-siddhesh/TEGD_thirdai_hackathon/blob/main/Thirdai_gdrive_engine_TEGD.ipynb)


## Note: We are not submitting the model, as our main Moto is to keep data private. You can just train your model on your own personal data.

#POCKETLLM