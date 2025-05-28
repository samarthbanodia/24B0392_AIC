# Transfer Learning on Fashion MNIST -Q2

In this question we had to adapt a pretrained CNN (ResNet50, VGG16 etc) to classify the Fashion MNIST data into 10 classes.

ResNet50 is considered a SOTA (state-of-the-art) model because of its unique architecture which allows training deep neural networks without the issue of vanishing gradients(by using residual networks).

## Local Setup 
- pip install matplotlib numpy pandas tensorflow scikit-learn

- Ensure you have cuda install for gpu utilisation as training is very heavy.
- run  jupyter notebook Q2.ipynb or python3 Q2.py

## ResNet50 Architecture

This is the architecture of ResNet50:

![ResNet50 Overview](attachment:396a1ebb-1e8a-4238-8e31-5ef2cb1e99ff:image.png)  
![ResNet50 Layers](attachment:ef3cff8f-84cc-420a-b215-6d92f5b43772:image.png)

Output from CNN layers are fed into FC layers which then map the features to the desired number of outputs.

---

## Transfer Learning

I used Transfer Learning to train the ResNet50 model to classify the Fashion MNIST dataset. TL is basically you freeze the backbone of a pretrained model (ie, make its layers untrainable — weights are fixed) and then add a classification head to classify on a custom dataset.

We can unfreeze some layers of the model to fine-tune it, which we had to do for this question.

---

## Flow of Model

- 1-D array of 784 size from grayscale Fashion MNIST .csv files. We can't directly input this as ResNet50 requires a 3-channel input (RGB).
- Reshape data to 28x28x1 (currently grayscale)
- Convert grayscale to RGB using duplication (grayscale_to_rgb)
- Resize to 224x224
- Above computation is done in batches using tf.data (https://www.tensorflow.org/guide/data) pipeline (earlier used a different method which caused memory crash)
- Into Sequential Model:  
  ResNet50 (frozen layers) → Flatten layer → Dense FC layer → Output layer
- After initial training, unfreeze a few deep layers, recompile and test the model again

---

## Experiments

- Fine-tuning learning rate
- Changing number of epochs
- Unfreezing different layers

---

## Error Handling and Troubleshooting

Earlier I was directly using:


tf.image.resize(rgb_image, [224,224]).numpy()

But memory got overloaded. It failed even after using CUDA and GPU. I even tried doing it in batches and later np.concatenate the batches but still the memory crashed.

Solution:
I found out there's something called the TensorFlow Data Pipeline (tf.data) which allows:

Multi-threaded processing on GPUs

Batch processing that avoids memory crashes

## Resources used :
 https://medium.com/@paravisionlab/supercharge-your-ai-resnet50-transfer-learning-unleashed-b7c0e40976c4

https://www.youtube.com/watch?v=JcU72smpLJk

https://youtu.be/KkIr1-fq5fo?si=GI7XKR4mygeacHNB

LR schdeduling : https://medium.com/@theom/a-very-short-visual-introduction-to-learning-rate-schedulers-with-code-189eddffdb00