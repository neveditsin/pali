# Pali Dataset

This repository contains the datasets used for our research project. 
Due to conference policy, this repository is anonymous. 
Below are the descriptions of the two main files in this repository: `train.xml` and `test.xml`.

## Files

### train.xml

- **Description**: The `train.xml` file contains the preprocessed training dataset used for our machine learning models. This dataset includes the following columns:
  - `Devanagari`: Contains text in the Devanagari script.
  - `Roman`: Contains transliterations of the Devanagari text into the Roman script.
  - `Label`: The target label (1: Theragatha, 2: Therigatha).

### test.xml

- **Description**: The `test.xml` file contains the preprocessed test dataset used to evaluate the performance of our machine learning models. This dataset includes the following columns:
  - `Devanagari`: Contains text in the Devanagari script.
  - `Roman`: Contains transliterations of the Devanagari text into the Roman script.
  - `Label`: The target label (1: Theragatha, 2: Therigatha).

## Usage

To use these datasets, you can read them into your preferred data analysis or machine learning environment. For example, using Python and pandas:

```python
import pandas as pd
import xml.etree.ElementTree as ET

def xml_to_df(xml_file):
    tree = ET.parse(xml_file)
    root = tree.getroot()

    data = []
    columns = ['Devanagari', 'Roman', 'Label']

    for row in root.findall('row'):
        entry = {col: row.find(col).text for col in columns}
        data.append(entry)

    return pd.DataFrame(data, columns=columns)

# Load the training dataset
train_df = xml_to_df('train.xml')

# Load the testing dataset
test_df = xml_to_df('test.xml')
```

## Citation

If you use this dataset, please cite:
```bibtex
@inproceedings{neveditsin-etal-2024-classification,
    title = "Classification of Buddhist Verses: The Efficacy and Limitations of Transformer-Based Models",
    author = "Neveditsin, Nikita  and
      Salgaonkar, Ambuja  and
      Lingras, Pawan  and
      Mago, Vijay",
    editor = {H{\"a}m{\"a}l{\"a}inen, Mika  and
      {\"O}hman, Emily  and
      Miyagawa, So  and
      Alnajjar, Khalid  and
      Bizzoni, Yuri},
    booktitle = "Proceedings of the 4th International Conference on Natural Language Processing for Digital Humanities",
    month = nov,
    year = "2024",
    address = "Miami, USA",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2024.nlp4dh-1.37/",
    doi = "10.18653/v1/2024.nlp4dh-1.37",
    pages = "377--385",
    abstract = "This study assesses the ability of machine learning to classify verses from Buddhist texts into two categories: Therigatha and Theragatha, attributed to female and male authors, respectively. It highlights the difficulties in data preprocessing and the use of Transformer-based models on Devanagari script due to limited vocabulary, demonstrating that simple statistical models can be equally effective. The research suggests areas for future exploration, provides the dataset for further study, and acknowledges existing limitations and challenges."
}
