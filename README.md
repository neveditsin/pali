# Anonymous Repository

This repository contains the datasets used for our research project. 
Due to conference policy, this repository is anonymous. 
Below are the descriptions of the two main files in this repository: `train.xml` and `test.xml`.

## Files

### train.xml

- **Description**: The `train.xml` file contains the preprocessed training dataset used for our machine learning models. This dataset includes the following columns:
  - `Devanagari`: Contains text in the Devanagari script.
  - `Roman`: Contains transliterations of the Devanagari text into the Roman script.
  - `Label`: The target label for testing.

### test.xml

- **Description**: The `test.xml` file contains the preprocessed test dataset used to evaluate the performance of our machine learning models. This dataset includes the following columns:
  - `Devanagari`: Contains text in the Devanagari script.
  - `Roman`: Contains transliterations of the Devanagari text into the Roman script.
  - `Label`: The target label for testing.

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
