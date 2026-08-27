# Metric Book Transcriber

A Jupyter notebook for transcribing birth records from historical metric books using the Google Gemini API.

## Overview

This project processes images of historical metric book pages and uses Gemini to extract/transcribe information from the records.

The project allows:

1. Choosing among different AI models, replacing one with another when the free plan is exhausted
2. Feeding the model with your own reference image with a corresponding manually transcribed text/table
3. Customizing the prompt to the AI according to your own requirements
4. Setting your own columns/fields in the resulting table depending on the targeted images and your wishes
5. Cropping pictures with a preview, so the AI processes only the necessary part of the page, excluding unwanted text
6. A transcription quality check after the first transcribed image
7. Checkpointing — so when the AI quota is exhausted, it starts next time from the not-yet-processed images
9. Export to a CSV file

The Gemini model `gemini-3.1-flash-lite` is currently used. It can be changed to any other model (`GEMINI_MODEL_NAME`). To navigate through models specialized for handwriting transcription, the [benchmark here](https://www.genea.ca/rankings/) was used. However, it compares only model performance on English/German handwritten texts.

The model `google/gemini-3.7-flash` was also tested but was significantly slower, and the free plan was exhausted after ~20 images. Although it processed the page number better, this didn't compensate for its drawbacks overall.

In both models' outcomes, hallucinations were detected — totally different text was sometimes present. The output CSV still needs careful post-processing. Better performance may be achieved by trial and error with different model / prompt / reference combinations to suit your own needs.

## Requirements

- Python 3.10+
- JupyterLab or Jupyter Notebook
- A Google Gemini API key

## Installation

Clone the repository:

```bash
git clone https://github.com/Owlly/metric_book_transcriber.git
cd metric_book_transcriber
```

Create a virtual environment:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Install the dependencies:

```bash
pip install -r requirements.txt
```

### API key

To get a Gemini API key:

1. Go to [Google AI Studio](https://aistudio.google.com/) and log in using your Google account.
2. Accept the terms of service if it is your first time visiting.
3. Click on **Get API key** in the left sidebar or at the bottom left corner of the screen.
4. Click the **Create API key** button. Select an existing project or create a new one when prompted.
5. Copy your newly generated alphanumeric key and store it **securely**.

Create your local `.env` file from the provided example:

```bash
cp .env.example .env
```

Then edit `.env`:

```
GEMINI_API_KEY=your_actual_api_key
```

The `.env` file is intentionally excluded from Git and **must never** be committed or shared.

## Usage

In your virtual environment, start JupyterLab:

```bash
jupyter lab
```

Open:

```
metric_book_transcriber_birth_resize-3.1flash.ipynb
```

The notebook uses one reference image (`007767501_01087.jpeg`) and a few example images in the folder `images/metr_book/`.

The reference image is used to "feed" Gemini together with the corresponding pre-transcribed table from this image as `metr_book_birth_ref.csv`. It's better to use your own pair of image and CSV (manually prepared), whose style is more representative of your targeted images.

Put your images into the folder `images/metr_book/` to process them with Gemini. Go through the notebook. Revise the output csv.

## License

This project is licensed under the **GNU General Public License v3.0 (GPL-3.0)**.

See the [LICENSE](LICENSE) file for the complete license text.
