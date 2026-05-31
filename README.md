# Sentiment Analysis App

A web-based sentiment analysis application using **VADER** and **RoBERTa** models built with Streamlit.

## Things with Sentiment Analysis different from other NLP tasks:
- **Subjectivity**: Sentiment is subjective and can vary based on context, culture, and individual interpretation.
- **Context Dependency**: The sentiment of a word or phrase can change based on the surrounding context (e.g., "not good" vs. "good").
- **Sarcasm and Irony**: These can be particularly challenging for sentiment analysis models to detect accurately. Models like RoBERTa, which are context-aware, can perform better in these cases compared to rule-based models like VADER.
- Removal of **stop words** can sometimes lead to loss of sentiment information, as certain stop words (e.g., "not") can significantly alter the sentiment of a sentence.
- Removal of **punctuation** can also affect sentiment analysis, as punctuation can convey emotions (e.g., "!" can indicate excitement or emphasis).
- **Other tasks** where we remove stop words and punctuation (e.g., **topic modeling**, **text classification**) may not be as sensitive to these elements, whereas sentiment analysis can be heavily influenced by them.

## Approaches

1) **VADER (Valence Aware Dictionary and sEntiment Reasoner)** : 
    * It breaks the text into words and looks up each word in its lexicon to determine its sentiment score.
    * It also considers the context of words (e.g., negations, intensifiers) and punctuation to adjust the sentiment scores accordingly.
    * It provides a compound score that summarizes the overall sentiment of the text, as well as individual scores for positive, negative, and neutral sentiments.
    * Unknown words are ignored, and the model relies on its predefined lexicon to analyze sentiment. This can lead to inaccuracies if the text contains slang, misspellings, or domain-specific language that is not included in the lexicon.
2) **RoBERTa (Robustly Optimized BERT Pretraining Approach)** :
    * It is a transformer-based model that has been fine-tuned for sentiment analysis tasks, including Twitter sentiment analysis.
    * It uses attention mechanisms to understand the context of words in a sentence, allowing it to capture nuances and subtleties in language that may affect sentiment.
    * It can handle shorthands, slang, and misspellings better than VADER due to its training on large datasets that include such variations.
    * The text needs to be tokenized and converted into a format suitable for the model, which can be more computationally intensive than VADER's rule-based approach.
    * With GPU acceleration, RoBERTa can provide faster inference times, but it can still run on CPU with reasonable performance for single inputs, though it may be slower than VADER.

## Features

- Input text area for user to enter review or comment text
- Option to select which models to use (VADER, RoBERTa, or both)
- Option to display the result as a bar chart or not

## Installation

1. Clone the repository:
   ```bash
    git clone https://github.com/PreyumKr/Semantic_Analyser.git
    cd Semantic_Analyser
    ```
2. Create a virtual environment and activate it:
   ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```
3. Install the required dependencies:
   ```bash
    pip install -r requirements.txt (for CPU)
    pip install -r requirements_gpu.txt (for GPU)
    ```
4. Run the Streamlit app:
   ```bash
    streamlit run streamlit_app.py
    ```
## Usage

1. Open the app in your browser (usually at `http://localhost:8501`).
2. Enter a review or comment in the text area.
3. Select which models to use for sentiment analysis (VADER, RoBERTa, or both). The settings are present in the sidebar, that can be accessed by clicking the "Settings" button in the top-left corner of the app.
4. Optionally, select whether to display the results as a bar chart.
5. Click the "Analyze Sentiment" button to see the results.

## Future Enhancements that can be done

- [ ] Save results to CSV
- [ ] Batch processing for multiple texts
- [ ] Emotion detection (e.g., joy, anger, sadness)
- [ ] Language support beyond English (e.g., multilingual models)

