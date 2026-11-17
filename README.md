# Mood Guesser

A beginner-friendly Python project that predicts whether a sentence expresses a **Happy** or **Sad** mood using keyword matching and a basic word-score learning approach.

This project was developed using **Google Colab** as part of the AIXcelerate selection task.

## Project Overview

The project explores two approaches to mood prediction:

- **Rule-Based Approach:** Uses manually selected clue words to predict the mood.
- **Learned Word-Score Approach:** Automatically learns word scores from labelled training examples.

## Level 1: Count the Moods

The `count_moods(data)` function counts the number of Happy and Sad sentences in the training dataset.

**Results:**
- Happy sentences: 8
- Sad sentences: 7

Output:
```text
(8, 7)
```

## Level 2: Guess the Mood

Two lists containing exactly 10 words each were created using the training dataset.

- `happy_words`: Contains 10 Happy clue words.
- `sad_words`: Contains 10 Sad clue words.

The `guess_mood(sentence)` function:
- Converts the sentence into lowercase.
- Removes punctuation.
- Counts matching Happy and Sad clue words.
- Predicts the mood based on the higher count.
- If there is a tie, it chooses Sad as the default.

## Level 3: Testing

**Accuracy on the 5 practice sentences: 80%**

### 1. Which sentence went wrong, and why?

The sentence **"Today was a great day"** was classified incorrectly as Sad.

Neither "today" nor "great" is present in the manually selected clue-word lists. Therefore, both Happy and Sad counts are zero, resulting in a tie. According to the tie-breaking rule, the program predicts Sad.

### 2. One change that would make my program better:

I could improve the program by adding more diverse training examples and expanding the clue-word vocabulary. I could also improve it to understand negation and sentence context instead of relying only on individual words.

## Learning Questions

### 1. Total score of "good party today" and its mood:

- good = +2
- party = +1
- today = 0

**Total score = +3**

Mood: Happy, because the total score is positive.

### 2. Total score of "bad exam day" and its mood:

- bad = -2
- exam = 0
- day = -1

**Total score = -3**

Mood: Sad, because the total score is negative.

### 3. Why did "exam" get a score of 0, and is that good or bad?

The word "exam" appears once in a Happy sentence and once in a Sad sentence. Therefore, its Happy count and Sad count are equal, resulting in a score of zero.

This is useful because the word "exam" alone does not indicate a particular mood. However, it also means the program cannot understand whether the exam experience was positive or negative from that word alone.

### 4. Why is "not good" labelled Happy by this method, and how could a program fix it?

The word "good" has a positive score of +2, while "not" has a score of zero. Since the program adds individual word scores without understanding sentence context, the total remains +2 and the sentence is labelled Happy.

This could be improved by detecting negation words such as "not" and reversing or reducing the score of the following word.

## Bonus: Learned Word-Score Model

The optional `learn_scores(data)` function automatically calculates word scores using the training dataset.

The `guess_mood_learned(sentence)` function uses these scores to predict the mood of a new sentence.

**Bonus model accuracy on the 5 practice sentences: 100%**

### Model Comparison

| Approach | Accuracy |
|---|---:|
| Rule-Based Model | 80% |
| Learned Word-Score Model | 100% |

The learned model performs better on these five practice sentences. However, this small test set does not guarantee good performance on unseen sentences. The model can also make mistakes when words are negated or used in different contexts.

## Tools and Technologies

- Python 3
- Google Colab
- GitHub

No external Python libraries are required.

## How to Run the Project

This project was developed and tested using Google Colab.

1. Open the `.ipynb` notebook in Google Colab.
2. Run the code cells from top to bottom.
3. View the mood predictions and accuracy results in the output.

The Python source code is also available in `main.py` and can be executed independently using:

```bash
python main.py
```

## Project Files

- `main.py` – Python implementation of Level 1, Level 2, Level 3, and the optional bonus.
- `README.md` – Project documentation, testing results, learning answers, and reflection.
- `screenshot.png` – Screenshot showing the program execution and output.
- `.ipynb` notebook – Google Colab notebook used for development and execution (if included).

## AI Declaration

**I used an AI tool: Yes.**

I used an AI tool for guidance in understanding the assignment, Python implementation, debugging, understanding the word-score learning method, and improving project documentation.

I reviewed the implementation and worked on understanding the logic behind the functions.

## Reflection

The most challenging part was selecting a limited number of clue words that could correctly identify the mood of different sentences.

Through this project, I learned how to process text by converting it to lowercase and removing punctuation, how to count word occurrences, and how to calculate prediction accuracy.

I also learned how a simple machine learning approach can automatically identify useful words from labelled examples using positive and negative scores.

Most importantly, I understood that a program can achieve good accuracy on a small dataset but still struggle with negation, context, and unfamiliar sentences.
