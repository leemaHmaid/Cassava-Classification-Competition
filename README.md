
# Cassava Disease Classification Project

In this repository, we have the code and results for classifying cassava leaf diseases using various machine learning models. The purpose of this project is to experiment with different models and techniques to achieve the best possible classification performance.

## Dataset

The dataset comprises:
- **Annotated Images**: 9,436 images of cassava leaves with labels.
- **Unlabeled Images**: 12,595 images of cassava leaves.

### Classes:
- Healthy
- Cassava Bacterial Blight (CBB)
- Cassava Brown Streak Disease (CBSD)
- Cassava Green Mottle (CGM)
- Cassava Mosaic Disease (CMD)

The dataset is sourced from LvdM (2024) and includes a diverse range of image quality and backgrounds, presenting challenges for accurate diagnosis (Mwebaze et al., 2019). The distribution of classes is unbalanced, with some classes underrepresented and symptoms sometimes showing multiple diseases in a single leaf.

## Experiments

### 1. First Experiment

In this initial experiment, we explored various models and their performance on the dataset:
- **Models Tested**: Custom CNN, ResNet50, ResNeXt50-32x4d, VGG19.
- **Techniques Used**: Basic data augmentation, 5 epochs, batch size of 32, SGD optimizer with a fixed learning rate, and no pre-trained weights.
- **Results**: The models struggled with poor generalization due to the dataset's imbalance and the simplicity of data augmentation techniques.

### 2. Second Experiment

Based on the first experiment's results, we enhanced our approach:
- **Augmentation**: Applied additional transformations such as vertical flip, shift-scale-rotate using the Albumentations library.
- **Cross-Validation**: Implemented 5-fold cross-validation.
- **Settings**: Fixed learning rate, no pre-trained weights.
- **Results**: Improved accuracy, but still below expectations.

| Method         | Accuracy (Experiment 1) | Accuracy (Experiment 2) |
|----------------|--------------------------|--------------------------|
| Custom CNN     | 10%                      | -                        |
| ResNet50       | 14%                      | 59%                      |
| ResNeXt50-32x4d| 15%                      | 73%                      |
| VGG19          | 16%                      | 64%                      |

### 3. Third Experiment

Building on the success of ResNeXt50-32x4d:
- **Improvements**: Added a classifier layer matching the number of classes, used 10 epochs, and adjusted the learning rate.
- **Observations**: Training and validation losses were high and oscillating, so a learning rate scheduler was introduced.
- **Results**: Accuracy improved to 78%.

### 4. Fourth Experiment

Exploring more complex models:
- **Model**: ResNeXt101-32x4d.
- **Enhancements**: Added layers to the backbone architecture, dropout, and average pooling. Reduced batch size to manage memory limitations.
- **Results**: Achieved the best accuracy of 90.4% on the private dataset.

## Conclusion

The experiments demonstrate that advanced models and enhanced data augmentation techniques significantly improve classification accuracy. The ResNeXt101-32x4d model with added layers and careful tuning achieved the highest performance, with a final accuracy of 90.4% on the private dataset, making it the most effective approach for this dataset.
