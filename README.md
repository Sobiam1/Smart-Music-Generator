# Smart-Music-Generator

We are going to explore the amplitude part of the music signal(Two components: Amplitude and Frequency) to predict the amplitude of the notes of a song based on the previous notes.

## Problematic
For this particular task, we will use Recurrent Neural Networks (RNN) and especially LSTMs which work well in cases of sequential data. They make predictions based on the current input as well as the previous ones instead of treating every beat in an independant way. This issue is compatible with the music since the musical beat depends on previous beats which makes the music a sequential data and LSTM model is best suited for this task.  

## Getting started

You can follow these steps to reproduce the same output:

1. Clone the repository or download the Ipyn file and run each cell to get each output and don't forget to include your music files paths.
2. The repo contains the IPython Notebook for prediction task and music files (ex) as input to learn from as well as a Readme file.                      
3. Run the ipynb to see the results. (if you can, try to compute on GPU environment to speed up the calculations ... Google Colab is a very good alternative and was chosen for this task)
To know more about it https://colab.research.google.com/notebooks/welcome.ipynb

## Prerequisites

 1. Python
 2. Pandas
 3. matplotlib
 4. numpy
 5. scipy
 6. Tensorflow
 7. Keras
 8. Pydub

## Results

We trained our two LSTMs models by feeding themtraining data from two songs and the output generated (in a .wav format) has predicted pretty well the music but to some extent, it is kind of distorted. To overcome this issue I tried different methods by tuning hyperparameters from adding the number of epochs to increasing number of layers without any radical change in the outcome.

Then I looked to the activation function (or transfer function), (-Activation functions' are used to introduce nonlinearity to models, which allows deep learning models to learn nonlinear prediction boundaries with different results ranges) but in this case, music data has negative values and the range of ReLU is "0 to +inf" which explains that our predictions will always have positive values. This is called the dying ReLU problem and as an attempt to solve it, we have the new ReLU function named "LeakyReLu" where our predictions can be also negative since the range of this function is "-inf to +inf".

This was a great win as you can predict for the output! Distortion has disappeared.
further checks: 
https://keras.io/activations/
https://stackoverflow.com/questions/46620286/artificial-neural-network-relu-activation-function-and-gradients


## Acknowledgments
In this task, I tried to generate samples of just two songs together. This work can be pushed further to build a multi-song model and increasing the look_back parameter to make more input features at the disposal of your model should you have a very good computing power. 
