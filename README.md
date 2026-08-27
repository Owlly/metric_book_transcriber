# Metric Book Transcriber

A Jupyter notebook for transcribing birth records from historical metric books using the Google Gemini API.

## Overview

This project processes images of historical metric book pages and uses Gemini to extract/transcribe information from the records.

The repository contains a small set of example images so that the notebook can be tested without publishing the full image collection.

## Requirements

- Python 3.10+
- JupyterLab or Jupyter Notebook
- A Google Gemini API key

## Installation

Clone the repository:

bash
git clone https://github.com/Owlly/metric_book_transcriber.git
cd metric_book_transcriber

Create a virtual environment:

python3 -m venv .venv
source .venv/bin/activate

Install the dependencies:

pip install -r requirements.txt

API key
To get a Gemini API key:
- Go to Google AI Studio and log in using your Google account.
- Accept the terms of service if it is your first time visiting.Open
- Click on Get API key in the left sidebar or at the bottom left corner of the screen.
- Click the Create API key button. Select an existing project or create a new one when prompted.
- Copy your newly generated alphanumeric key and store it **securely**.

Create your local .env file from the provided example:

cp .env.example .env

Then edit .env:

GEMINI_API_KEY=your_actual_api_key

The .env file is intentionally excluded from Git and **must never** be committed or shared.

**## Usage**

In your virtual environment, start JupyterLab:

jupyter lab

Open:

metric_book_transcriber_birth_resize-3.1flash.ipynb

The notebook uses the example images in:

images/metr_book/

The example image (007767501_01087.jpeg) is used to "feed" Gemini as a reference together with the corresponding pre-transcribed image as metr_book_birth_ref.csv table. Better to use your own pair image and csv (manually prepared), which style is more representative to your targeted images. 

Put your images to the folder images/metr_book/ to process with Gemini.

