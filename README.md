# Traffic
Writing an AI with TensorFlow to identify which traffic sign appears in a photograph

# Experiments

## 1st Experiment
| Layer | Filter | Kernel Size | Activation |
| --- | --- | --- | --- |
| Conv2D | 30 | 5 | relu |
| Conv2D | NUM_CATEGORIES | 3 | relu |
| MaxPooling2D | | 3 | |
| Flatten | | | |
| Dense | NUM_CATEGORIES | | softmax |

**NUM_CATEGORIES:** 3

**Accuracy:** 0.66

I used the small dataset for all trials to compare different networks' accuracy.

## 2nd Experiment
| Layer | Filter | Kernel Size | Activation |
| --- | --- | --- | --- |
| Conv2D | 30 | 5 | relu |
| AveragePooling2D | | 2 | |
| Conv2D | NUM_CATEGORIES | 3 | sigmoid |
| MaxPooling2D | | 3 | |
| Flatten | | | |
| Dense | NUM_CATEGORIES | | softmax |

**Accuracy:** 0.46->0.55

I attempted with a different activation function, the sigmoid function, for the second convolutional layer instead of relu. I also added an average pooling layer. However, the accuracy decreased to at least 0.4635, significantly lower than the last trial. It is clear that changing the activation function and adding a pooling layer does not work well.

## 3rd Experiment
| Layer | Filter | Kernel Size | Activation |
| --- | --- | --- | --- |
| Conv2D | 30 | 5 | relu |
| Conv2D | NUM_CATEGORIES | 3 | sigmoid |
| MaxPooling2D | | 3 | |
| Flatten | | | |
| Dense | NUM_CATEGORIES | | softmax |

**Accuracy:** 0.45->0.48

I took a step back by deleting the extra average pooling layer and kept the sigmoid activation function. The average accuracy is even lower, which proved that the sigmoid activation function did not work.

## 4th Experiment
| Layer | Filter | Kernel Size | Activation |
| --- | --- | --- | --- |
| Conv2D | 30 | 5 | relu |
| Conv2D | NUM_CATEGORIES | 3 | relu |
| MaxPooling2D | | 5 | |
| Flatten | | | |
| Dense | NUM_CATEGORIES | | softmax |

**Accuracy:** 0.47->0.48

This time, I changed the sigmoid function back to relu activation while slightly adjusting the pool size in the 2D max pooling from 3 to 5. But the accuracy is still very low. Combined with the result from the last experiment, knowing that the activation function should stay as relu, I was left with the option: number of filters.

# 5th Experiment
| Layer | Filter | Kernel Size | Activation |
| --- | --- | --- | --- |
| Conv2D | 100 | 5 | relu |
| Conv2D | 80 | 3 | relu |
| MaxPooling2D | | 5 | |
| Flatten | | | |
| Dense | NUM_CATEGORIES | | softmax |

**Accuracy:** 0.57->0.98

I increased the number of neurons for the first layer from 30 to 100 and for the second layer from 3 to 80. Going through 10 epochs, the accuracy raised from 0.57 to 0.98, which works very well.

# What I Noticed

As the number of filters increases, the accuracy would go up. Adding more pooling layers and using a sigmoid function can potentially decrease accuracy.
