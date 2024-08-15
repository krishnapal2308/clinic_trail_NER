# Named Entity Recognition for Clinical Trials Using Continual Learning

## Problem Statement

This project focuses on developing a Named Entity Recognition (NER) system for clinical trial data using a BERT-based model enhanced by continual learning techniques. The goal is to identify and classify medical entities—such as treatments, chronic diseases, cancers, and allergies—across multiple datasets while continuously adapting to new information and preserving previously learned knowledge.

### Key Objectives:

1. Develop a BERT-based NER model for medical entity recognition in clinical trial texts.
2. Utilize continual learning to train the model across multiple datasets, reflecting real-world scenarios where new data is introduced over time.
3. Assess the model's performance in terms of knowledge retention, forward and backward transfer, and maintaining a fixed model capacity.
4. Compare continual learning with traditional joint training on combined datasets.
5. Evaluate entity-wise and weighted average F1 scores to gauge the model's effectiveness across various medical entities.
6. Address challenges related to imbalanced data, particularly in recognizing rare entity types.

This project highlights the application of advanced NLP techniques in healthcare, demonstrating the effectiveness of continual learning in creating up-to-date and comprehensive medical entity recognition systems.

## Methodology

The approach utilizes a BERT model for token classification, implemented using the Hugging Face Transformers library. The continual learning process involves:

1. **Data Preprocessing:** Cleaning and encoding the data with a BIO (Beginning, Inside, Outside) tagging scheme.
2. **Model Training:** Iterative training on multiple datasets (G1, G2, G3) while retaining a subset of examples from previous tasks.
3. **Evaluation:** Assessing performance using entity-wise and weighted average F1 scores.
4. **Comparison:** Benchmarking against a jointly trained model on the combined dataset.

For detailed implementation, please refer to the attached `Clinic_Trial_NER.ipynb` file.

## Results

The continual learning approach demonstrated significant improvements:

1. Gradual improvement in overall performance, particularly in the weighted average F1 score.
2. Successful mitigation of catastrophic forgetting (Knowledge Retention) by retaining a small subset of examples from previous tasks.
3. The continually trained model outperformed the jointly trained base model on the combined test set.
4. Improved ability to recognize rare entities (like allergies) as more data was added.

| Metric               | Task 1 | Task 2 | Task 3 | Combined | Base Model |
|----------------------|--------|--------|--------|----------|------------|
| Treatment F1         | 0.6489 | 0.6794 | 0.7009 | 0.7525   | 0.7181     |
| Chronic Disease F1   | 0.7071 | 0.7013 | 0.7126 | 0.7958   | 0.7401     |
| Cancer F1            | 0.6220 | 0.6618 | 0.6947 | 0.7358   | 0.6750     |
| Allergy F1           | 0.1250 | 0.7111 | 0.7000 | 0.7339   | 0.6978     |
| Weighted Average F1  | 0.6589 | 0.6866 | 0.7048 | 0.7669   | 0.7204     |

## Future Work

1. Explore more sophisticated continual learning techniques, such as Elastic Weight Consolidation (EWC).
2. Implement adaptive sampling methods for memory replay, such as diversity-based sampling.
3. Investigate the impact of different model architectures and pre-training approaches on continual learning performance.
4. Extend the system to handle a wider range of medical entities and explore cross-domain transfer learning.