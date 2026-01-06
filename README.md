# Image Captioning with BLIP

This project leverages state-of-the-art Deep Learning models to automatically generate descriptive text for images. By utilizing the **BLIP (Bootstrapping Language-Image Pre-training)** model from Salesforce, the application can "see" an image and provide a human-readable caption.

---

## 🎯 Objective
The primary goal of this project is to provide a seamless interface for generating accurate image descriptions. It offers two modes of operation:
* **Interactive Mode:** A Gradio-based web UI for real-time, single-image captioning.
* **Batch Mode:** An automated pipeline to process entire directories of images and export results to structured formats like text and Excel.

## 🌉 The Gap It Fills
Manual image tagging and captioning are incredibly time-consuming, subjective, and prone to human error. This project bridges the gap between **Computer Vision** and **Natural Language Processing (NLP)**, providing a way to convert visual data into searchable, descriptive text without manual intervention.

## 💡 Why It Is Important
* **Accessibility:** Automated captions can generate "Alt-text" for visually impaired users, making web content more inclusive.
* **SEO & Searchability:** By converting images into text, databases and websites become searchable via keywords found in the captions.
* **Content Management:** Massive libraries of digital assets can be organized and categorized automatically.
* **Efficiency:** Automating batch processing saves hours of manual data entry for researchers and content creators.



---

## 🛠️ Tech Stack
This project is built using the following libraries and frameworks:
* **Language:** Python
* **Deep Learning Framework:** `transformers` (Hugging Face)
* **Model:** `Salesforce/blip-image-captioning-base`
* **Interface:** `gradio`
* **Image Processing:** `PIL` (Pillow) and `numpy`
* **Data Management:** `pandas` (for Excel exporting) and `glob/os`

---

## ⚙️ How It Functions
The project follows a standard machine learning pipeline:
1. **Preprocessing:** Images are converted to RGB format and processed using the `AutoProcessor`.
2. **Inference:** The processed image is passed into the `BlipForConditionalGeneration` model.
3. **Decoding:** The model's numerical output is decoded back into human-readable text using `processor.decode`.
4. **Output:** * The Gradio UI displays the caption directly to the user.
    * The batch processor iterates through a directory, saving captions into `captions.txt` and a structured `Caption_df.xlsx` spreadsheet.

---

## 🚀 Upgrading to BLIP-2
For users requiring higher accuracy and more sophisticated descriptions, this project includes optional support for **BLIP-2**. 

### How to Implement
To switch to BLIP-2, replace the model loading section in the code with the following snippet:
```python
from transformers import Blip2Processor, Blip2ForConditionalGeneration 

# Load the pretrained processor and model
processor = Blip2Processor.from_pretrained("Salesforce/blip2-opt-2.7b")
model = Blip2ForConditionalGeneration.from_pretrained("Salesforce/blip2-opt-2.7b")
# Note: The BLIP-2 model (blip2-opt-2.7b) is significantly more powerful but requires approximately 10GB of space.
