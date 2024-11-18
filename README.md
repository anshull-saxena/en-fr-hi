
# Multilingual Translation Program

This project provides a multilingual translation program that supports translation between **English**, **French**, and **Hindi** using pretrained MarianMT models from the Hugging Face library. 

You can access the files for this project through:
- **GitHub Repository:** [en-fr-hi](https://github.com/anshull-saxena/en-fr-hi)
- **Zipped File:** [Google Drive](https://drive.google.com/file/d/1sOA29hnZzp5I8xqrefNOrGhvlh3TWUWD/view?usp=sharing)

## Features
- Translation from **English → French** and **English → Hindi**
- Translation from **French → English** and **Hindi → English**
- Chained translations across languages (e.g., French → English → Hindi) *(Note: Chained translations are currently not fully functional, as English to Hindi and vice versa are not accurate. We are working on improving this.)*
- Automatic dependency installation for seamless setup

---

## Prerequisites

### Software Requirements
- **Python 3.8 or higher** (make sure Python is properly installed on your system)
- **pip** (Python package manager)

---

## Installation and Setup

1. Clone the repository or download the zipped file from the links above:
   ```bash
   git clone https://github.com/anshull-saxena/en-fr-hi.git
   cd en-fr-hi
   ```

2. Install the required dependencies:
   ```bash
   pip install torch transformers sentencepiece sacremoses
   ```

   Alternatively, the program automatically installs dependencies on its first run.

3. Ensure the model checkpoints (`en_to_fr_model_checkpoint`, `en_to_hi_model_checkpoint`, etc.) are in the same directory as the script.

---

## Usage

To run the program:
1. Execute the script:
   ```bash
   python test.py
   ```
2. Follow the prompts:
   - Enter the input language (**english**, **french**, or **hindi**)
   - Choose the target language from the available options
   - Enter the sentence to translate

3. The program will provide the translated sentence. For chained translations, intermediate languages are automatically handled.

---

## Example

**Input:**
- Input Language: `english`
- Target Language: `french`
- Sentence: `Hello, how are you?`

**Output:**
- Translated Sentence: `Bonjour, comment allez-vous ?`

---

## Project Structure

```
en-fr-hi/
│
├── en_to_fr_model_checkpoint/       # Model checkpoint for English → French
├── en_to_hi_model_checkpoint/       # Model checkpoint for English → Hindi
├── fr_to_en_model_checkpoint/       # Model checkpoint for French → English
├── hi_to_en_model_checkpoint/       # Model checkpoint for Hindi → English
├── test.py                          # Main Python script for the program
└── README.md                        # Documentation
```

---

## Notes
1. Ensure that the directory contains all model checkpoints before running the script.
2. If using the Google Drive link, extract the zipped file to access the required files.
3. The program automatically handles dependency installation if they are missing.

---

## License

This project is open-source and available under the **MIT License**. Feel free to use and modify it as needed.
