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

```bash
git clone https://github.com/Owlly/metric-book-transcriber.git
cd metric-book-transcriber
Create a virtual environment:

python3 -m venv .venv
source .venv/bin/activate

Install the dependencies:

pip install -r requirements.txt
API key

The notebook requires a Gemini API key.

Create your local .env file from the provided example:

cp .env.example .env

Then edit .env:

GEMINI_API_KEY=your_actual_api_key

The .env file is intentionally excluded from Git and must never be committed or shared.

Usage

Start JupyterLab:

jupyter lab

Open:

metric_book_transcriber_birth_resize-3.1flash.ipynb

The notebook uses the example images in:

images/metr_book/

and the reference data in:

metr_book_birth_ref.csv
Input data

The repository contains only a few example images.

The full historical image collection is not included because of its size.

To process a larger collection, update the input directory in the notebook:

INPUT_IMAGES_DIR = Path("images/metr_book")
Project structure
.
├── images/
│   └── metr_book/
├── metr_book_birth_ref.csv
├── metric_book_transcriber_birth_resize-3.1flash.ipynb
├── requirements.txt
├── .env.example
├── .gitignore
└── README.md
License

TODO


Save:

**Ctrl+O → Enter → Ctrl+X**

### One thing I intentionally left as `TODO`

**Don't choose a license yet.**

Because this is a public repository, the license matters: it determines what other people are legally allowed to do with your code. We can choose an appropriate one after you tell me whether you want others to:

- freely use/modify it, including commercially;
- freely use it but preserve attribution/license;
- or have more restrictions.

---

# Step 30 — Add Jupyter to `requirements.txt`

There's one issue with our current `requirements.txt`.

We identified the packages imported by your notebook, but someone cloning the repository also needs Jupyter to actually run it.

Let's change it to:

```text
pandas
Pillow
python-dotenv
google-genai
jupyterlab

Run:

nano requirements.txt

Replace the contents with those five lines.

Save and exit.
