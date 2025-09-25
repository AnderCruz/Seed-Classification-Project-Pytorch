# Seed Classification Project Using Pythoch

## Overview

This project, developed by [Nowaanalytics.com](https://nowaanalytics.com), implements a neural network using PyTorch to classify seeds based on their physical characteristics. The dataset used is `sementes.csv`, which contains features such as area, perimeter, compactness, length, width, asymmetry, and groove length, with the target variable being the seed species (represented as integers 0, 1, or 2). The code is written in a Jupyter Notebook (`sementes.ipynb`) and demonstrates data preprocessing, model training, and evaluation.

The project performs the following tasks:
- Loads and preprocesses the seed dataset.
- Splits the data into training and testing sets.
- Defines and trains a neural network model using PyTorch.
- Evaluates the model's performance on the test set by comparing predicted and actual labels.

## Dataset

The dataset (`sementes.csv`) is sourced from [this URL](https://raw.githubusercontent.com/alura-cursos/Primeiros_passos_pytorch/main/sementes.csv). It contains the following columns:
- **Área**: Area of the seed.
- **Perímetro**: Perimeter of the seed.
- **Compacidade**: Compactness of the seed.
- **Comprimento**: Length of the seed.
- **Largura**: Width of the seed.
- **Assimetria**: Asymmetry coefficient.
- **Comprimento do sulco**: Length of the seed groove.
- **Espécie**: Target variable (seed species, encoded as 0, 1, or 2).

## Requirements

To run the notebook, you need the following Python libraries:
- `pandas`
- `scikit-learn`
- `torch`
- `numpy` (implicitly used by pandas and PyTorch)

You can install the required libraries using pip:

```bash
pip install pandas scikit-learn torch
```

## Project Structure

- `sementes.ipynb`: The main Jupyter Notebook containing the code for loading data, preprocessing, training the neural network, and evaluating the model.
- `README.md`: This file, providing an overview and instructions for the project.

## Code Explanation

The `sementes.ipynb` notebook includes the following steps:

1. **Data Loading and Preprocessing**:
   - The dataset is loaded from a CSV file using `pandas`.
   - Features are separated from the target variable (`Espécie`), and the data is converted to NumPy arrays.
   - The dataset is split into training (80%) and testing (20%) sets using `train_test_split` from `scikit-learn`.
   - The data is converted to PyTorch tensors (`FloatTensor` for features, `LongTensor` for labels).

2. **Neural Network Model**:
   - A custom neural network class `Modelo` is defined using `torch.nn.Module`.
   - The model has three fully connected layers:
     - Input layer (7 features) to 14 units (first hidden layer).
     - First hidden layer (14 units) to 49 units (second hidden layer).
     - Second hidden layer (49 units) to 3 units (output layer for 3 classes).
   - ReLU activation is applied after the first two layers.

3. **Training**:
   - The model is trained for 100 epochs using the Adam optimizer (learning rate = 0.01) and `CrossEntropyLoss` as the loss function.
   - The training loop computes predictions, calculates the loss, and updates the model parameters using backpropagation.

4. **Evaluation**:
   - Predictions are made on the test set without gradient computation.
   - A pandas DataFrame is created to compare true labels (`Y`), predicted labels (`YHat`), and a correctness indicator (`Correto`).

## How to Run

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   cd your-repo-name
   ```

2. **Set Up the Environment**:
   Ensure you have Python installed (version 3.6 or higher recommended). Install the required libraries:
   ```bash
   pip install -r requirements.txt
   ```
   Alternatively, install the libraries manually as listed above.

3. **Run the Notebook**:
   - Open Jupyter Notebook:
     ```bash
     jupyter notebook
     ```
   - Navigate to `sementes.ipynb` and run all cells to execute the code.
   - The notebook will load the dataset, train the model, and display the prediction results.

## Results

The notebook outputs a DataFrame showing:
- True labels (`Y`).
- Predicted labels (`YHat`).
- A `Correto` column indicating whether the prediction was correct (1) or incorrect (0).

The model's performance can be evaluated by analyzing the proportion of correct predictions in the test set.

## Contributing

This project was developed by [Nowaanalytics.com](https://nowaanalytics.com). Contributions are welcome! If you have suggestions for improvements or new features:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature/your-feature`).
3. Make your changes and commit (`git commit -m 'Add your feature'`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Open a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

- The dataset is provided by [Alura](https://www.alura.com.br/) via the course "Primeiros Passos com PyTorch."
- Developed by [Nowaanalytics.com](https://nowaanalytics.com).
