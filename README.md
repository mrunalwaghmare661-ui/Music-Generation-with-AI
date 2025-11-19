# Music-Generation-with-AI
Automatic Music Generation using AI
Mrunal Waghmare- mrunalwaghmare661
An automatic music generation model which has been trained on schubert piano tones can be used to generate piano music .

Table of Contents
About The Project
Built With
Getting Started
Prerequisites
Installation
Usage
About The Project
In this project we have created a LSTM based model which takes in a seed input in form of notes ,32 notes in particular. It then predicts future notes as required. We had experimented with two types of models for this project.

LSTM based RNN model
1D convolution based model with skip connections and Residual networks inspired from Wavenet architechture
LSTM Based Model
Long Short-Term Memory (LSTM) networks are a type of recurrent neural network capable of learning order dependence in sequence prediction problems. A typical LSTM cell looks like one shown below:


These cells are then linked in chain form to form a LSTM network. These LSTM networks are then stacked upon one another such that output of one chain is input to the other. Complete LSTM model description can be found in Model/LSTM.py.


1D Convolution based Wavenet inspired Model
1D convolutions are similar to 2D convolutions if you are familiar with CNNs. Such 1D convolutional networks can be used to train models as an efficient alternative to recurrent neural networks. Wavenets use modified version of these 1D convolutions called as Dilated convolutions. Dilated convolutions help in increasing the receptive field of the network.


These convolutions layers when used with proper padding can be stacked and used along with residual connections and skip connections and then passed to fully connected layers to predict next musical note.

Wavenet architechture

The complete description of the wavenet based model can be found in Models/Wavenet.py

After experimenting with both the models , we observed that Wavenet model was a bit complex for training piano musical notes. It trained properly but the training process was a bit time consuming. Although we tested the Wavenet model to predict simple sinosoids , to test its validity , with varying frequencies and it performed very well on them.

We finally decided to go with LSTM based model.

Training details
The model was trained on GeForce GTX 1080 Ti GPU for about 2.5 - 3 hours .
The complete output training log can be found in /op_file.txt
In initial 25 epoch , we predicted only the next note; from epoch 25 to epoch 44 next 4 notes were predicted and from epoch 45 to epoch 90, next 8 notes were predicted.
Loss History

Training Accuracy
Mode	Correct predictions	Total predictions	Accuracy
Training	406824	448760	90.65513
Validation	110044	128224	85.82168
Testing	55016	64112	85.81232
Results
All the generated music files can be found in /Outputs directory . These files are stored as .mid extensions. Instructions to play these files have been given below.

I converted some of them to MP3 and changed the speed since the predicted notes are mere notes and have no sense of tempo. Enjoy listening to the melodious beats 😉
Track 1
Track 2
Track 3

Built With
The following technologies were used to build the project

Pytorch
Tensorflow
Music21
Getting Started
Installation
Clone the repository
https://github.com/mrunalwaghmare661-ui/Music-Generation-with-AI
Create and Activate Virtual Environment
cd Music_Gen_AI
python3 -m venv /path_to_new_virtual_environment
source /path_to_new_virtual_environment/venv/bin/activate
Install the dependancies
pip3 install requirements.txt
You can either train your own model by running train.py

python3 train.py
If you want to run Notebook version of the training code , you can start a jupyter server and start training in jupyter notebook

cd Music_Gen_AI
jupyter notebook
Now open the Music_Gen_AI_Train.ipynb notebook.

Running Testing notebook
If you want to test the results on our pretrained model stored in /Trained_Models you can open Music_Gen_AI_Test.ipynb notebook on jupyter server.

All the outputs will be stored as .midi files in Outputs directory. To Listen to these raw midi files you need timidity.

sudo apt-get update
sudo apt-get install timidity
#to run the music1.mid file
timidity music1.mid
If you want to listen to the mp3 version , you can use online midi to mp3 converters like
Online Midi to MP3 converter
Since the music generated is are notes and there is no sense of tempo, we can used online tools to speed up the mp3 music and listen to the melodious piano beats.

MP3 Speed changer
