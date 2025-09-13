# Stack Overflow Question Quality Predictor and Suggester

This project is designed to improve the quality of questions on platforms like Stack Overflow. It uses a **BERT-based deep learning model** to classify question quality and an **information retrieval system** to provide actionable suggestions when a question is flagged as low quality.

---

### Key Features

* **Quality Classification**

  * Predicts whether a question is:

    * High Quality (`HQ`)
    * Low Quality – Needs Edit (`LQ_EDIT`)
    * Low Quality – Needs Close (`LQ_CLOSE`)

* **Actionable Suggestions**

  * Provides clear feedback for low-quality questions (e.g., add error messages, include code, improve clarity).

* **Pattern Learning**

  * Analyzes high-quality questions to learn features such as average title/body length, code snippets, and error reporting.

* **Information Retrieval Support**

  * Uses **TF-IDF** for keyword-based matching and **Sentence-BERT (SBERT)** for semantic similarity.
  * Retrieves examples of similar, well-written questions to guide improvements.

---

### Setup

1. Clone or download the repository.
2. Install the required dependencies:

   ```bash
   pip install -r requirements.txt
   ```
3. Prepare the dataset:

   * Place `train.csv` and `valid.csv` inside a `dataset/` folder.
   * Each file must contain:

     * `Title` (question title)
     * `Body` (question body)
     * `Y` (label: `HQ`, `LQ_EDIT`, or `LQ_CLOSE`)

---

### Usage

#### 1. Train the Model

Run:

```bash
python question_quality_predictor.py
```

This will:

* Preprocess the data and fine-tune the BERT model.
* Generate performance graphs (`accuracy_loss.png`).
* Create a confusion matrix (`confusion_matrix.png`).
* Save the trained model as `bert_stackoverflow_model.pth`.

#### 2. Get Suggestions for a Question

Run:

```bash
python suggestion_model.py
```

Then:

* Enter a question title and body.
* The system predicts quality.
* If the question is low-quality, it provides improvement tips and shows similar high-quality examples.

---

### Outputs

* **accuracy\_loss.png**: Training and validation accuracy/loss curves.
* **confusion\_matrix.png**: Classification results by category.
* **bert\_stackoverflow\_model.pth**: Saved trained model.


### Future Improvements

* Integrate with a web-based UI for real-time feedback.
* Extend dataset with more diverse questions.
* Add additional features like grammar checking and code snippet validation.

