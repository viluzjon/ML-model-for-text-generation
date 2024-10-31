# Text Generation from Debate Transcript

This model generates vaguely coherent text based on a transcript from the presidential debate between K. Harris and D. Trump that took place on September 11, 2024. 
The transcript is processed using a trigram model to create sentences. The code is designed to run in Google Colab.
The input text file can be swapped with a file of your choice, in which case:
- the upload link needs to be updated (line 17)
- the txt file name needs to be updated (lines 16, 31, 90)
*Works wonders with religious sermons*

Let this be a test of absurd.

# Usage

Clone this repository or download the files.
Make sure the transcript file (harris-trump-transcript.txt) is available in the same directory.
Run the main script in Google Colab to generate text based on the transcript.
The generated text will be saved to generated_text.txt.

# Source of Transcript

The transcript used in this project is from the 9/11 2024 debate available on YouTube: https://www.youtube.com/watch?v=VgsC_aBquUE.
