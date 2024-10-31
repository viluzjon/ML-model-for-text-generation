pip install nltk

import nltk
from nltk import word_tokenize
from nltk.util import ngrams
from collections import defaultdict, Counter
import random

!pip install gdown

!pip install youtube-transcript-api

import gdown

# Pulling data
output = "harris-trump-transcript.txt"
data = gdown.download(f"https://raw.githubusercontent.com/viluzjon/ML-model-for-text-generation/refs/heads/main/harris-trump-transcript.txt", output, quiet=False)

import nltk
nltk.download('punkt')

import nltk
from nltk.tokenize import word_tokenize

# Word tokenization
def load_data(file_name):
    with open(file_name, 'r', encoding='utf-8') as file:
        text = file.read()
    return text.lower()

file_name = 'harris-trump-transcript.txt'
text_data = load_data(file_name)
tokens = word_tokenize(text_data)

# Creating trigram model based on text provided
trigrams = list(ngrams(tokens, 70))

trigram_model = defaultdict(Counter)

for trigram in trigrams:
    trigram_model[(trigram[0], trigram[1])][trigram[2]] += 1

import random
import re

# Creating a generate text function

def generate_text(model, num_words=1000, text=None):
    # Split the text into words and randomly choose two seeds
    words = text.split()

    # Randomly select two words from the text
    starting_words = random.sample(words, 2)
    sentence = list(starting_words)

    for _ in range(num_words):
        try:
            # Get probabilities of next words
            next_word_probs = model[tuple(sentence[-2:])]

            # Word sampling based on probabilities
            next_word = random.choices(list(next_word_probs.keys()), weights=list(next_word_probs.values()))[0]
        except (KeyError, IndexError):
            # Handle the case where there's no entry for the current tuple
            next_word = random.choice(list(model.keys()))[0]

        # Add the next word to the sentence
        sentence.append(next_word)

    # Join the sentence into a string
    text = ' '.join(sentence)

    # Capitalize the first letter of the output text
    text = text[0].upper() + text[1:]

    # Capitalize the first letter of each sentence
    text = re.sub(r'(?<=\.|\?|!)\s*(\w)', lambda match: match.group(1).upper(), text)

    # Remove space before punctuation
    text = text.replace(' ,', ',').replace(' .', '.').replace(' !', '!').replace(' ?', '?')

    # Add space after punctuation
    text = re.sub(r'([.?!])(\s*)(\w)', r'\1 \3', text)  # Ensures a space after ., ?, ! before the next word

    return text

def main():
    # Read the transcript from the file
    try:
        with open('harris-trump-transcript.txt', 'r') as file:
            transcript_text = file.read()
    except FileNotFoundError:
        print("The file 'transcript.txt' was not found.")
        return

    # Text generation
    generated_text = generate_text(trigram_model, text=transcript_text)
    print(generated_text)

    # Saving output to a file
    with open("generated_text.txt", "w") as file:
      file.write(generated_text)

# Run the main function
main()

from google.colab import files
files.download("generated_text.txt")
