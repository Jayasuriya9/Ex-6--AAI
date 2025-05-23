## Date: 15.05.2025

<h1 align="center">  
   Experiment 6: Implementation of Semantic Analysis
</h1>  

### Name: J Jayasuriya
### Register Number: 212223230088

## Aim: 
To perform Parts of speech identification and Synonym using Natural Language Processing (NLP) techniques. 

## Algorithm:
#### Step 1: 
Import the nltk library.
#### Step 2: 
Download the 'punkt', 'wordnet', and 'averaged_perceptron_tagger' resources.
#### Step 3:
Accept user input for the text.
#### Step 4:
Tokenize the input text into words using the word_tokenize function.
#### Step 5:
Iterate through each word in the tokenized text.

•	Perform part-of-speech tagging on the tokenized words using nltk.pos_tag.

•	Print each word along with its corresponding part-of-speech tag.

•	For each verb , iterate through its synsets (sets of synonyms) using wordnet.synsets(word).

•	Extract synonyms and antonyms using lemma.name() and lemma.antonyms()[0].name() respectively.

•	Print the unique sets of synonyms and antonyms.

## Program:
```py

import nltk
from nltk.corpus import wordnet

nltk.download('punkt')
nltk.download('averaged_perceptron_tagger')
nltk.download('wordnet')

def get_synonyms(word):
    synonyms = set()
    for syn in wordnet.synsets(word):
        for lemma in syn.lemmas():
            synonyms.add(lemma.name())
    return synonyms

def process_text_file(file_path):
    with open(file_path, 'r') as file:
        text = file.read()
    return text  # Return the processed text

text = process_text_file('sample.txt')
print("Original Text: ")
with open('sample.txt', 'r') as file:
    content = file.read()
    print(content)
    print("\n")

# Tokenize the text into sentences
sentences = nltk.sent_tokenize(text)

for sentence in sentences:
    # Tokenize each sentence into words
    words = nltk.word_tokenize(sentence)

    # Perform part-of-speech tagging
    pos_tags = nltk.pos_tag(words)

    # Extract verbs
    verbs = [word for word, pos in pos_tags if pos.startswith('V')]

    # Get synonyms for each verb
    for verb in verbs:
        synonyms = get_synonyms(verb)
        print(f"Verb: {verb}")
        print(f"Synonyms: {', '.join(synonyms)}\n")

```
## Sample Input File:
![Screenshot 2024-11-11 at 2 33 23 PM](https://github.com/user-attachments/assets/2a280839-322b-4258-95d8-881d02ec1fc7)


## Output:
![Screenshot 2024-11-11 at 2 21 02 PM](https://github.com/user-attachments/assets/d94df0d2-2e37-41a9-83c6-4ce1222bad2d)

## Result:
Thus, the program to perform the Parts of Speech identification and Synonymis executed sucessfully.
