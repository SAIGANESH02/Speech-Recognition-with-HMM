## Speech recognition using HMM	
[Project Link](https://github.com/SAIGANESH02/Speech-Recognition-with-HMM/)

### Introduction
- Speech recognition is a challenging problem on which much work has been done the last decades. Some of the most successful results have been obtained by using hidden Markov models as explained by Rabiner in 1989. 
- A well working generic speech recognizer would enable more efficient communication for everybody, but especially for children, analphabets and people with disabilities. A speech recognizer could also be a subsystem in a speech-to-speech translator. 
- The speech recognition system implemented during this project trains one hidden Markov model for each word that it should be able to recognize. The models are trained with labeled training data, and the classification is performed by passing the features to each model and then selecting the best match.

### Markov Chain Model
- A stochastic model that describe the probabilities of transition among the states of a system. 
- It is a random process that undergoes transitions from one state to another on a state space.
- Change of states depends probabilistically only on the current state of the system

### System FLow Chart
![image](https://user-images.githubusercontent.com/53213766/174874526-7b87cf5b-d42e-4ca0-8465-3ed4a13f0d1d.png)

### Feature Extraction
The source speech is quantized with 16 bits and sampled at 8000 Hz. The signal is divided into 80-sample frames, each equivalent to 10 milliseconds of speech. With 20 samples on each side, the frames overlap. Because of the  throat's limited flexibility, the speech is close to stationary for this short period of time, according to the theory. We'll extract our features from the frequency domain, but before doing so with the fast Fourier transform, we'll multiply by a Hamming window to limit spectrum leakage caused by signal framing.

![image](https://user-images.githubusercontent.com/53213766/174875939-e315e6a3-13a8-4dc5-8a04-2ea125dcd0c3.png)

### Forward Algorithm
- Used to calculate a belief state: the probability of a state at a certain time, given the history of evidence
- Used to select the model (i.e. word)that most likely generated the speech signal
![image](https://user-images.githubusercontent.com/53213766/174876074-a1f07da6-09a8-466d-9787-008b454fabbc.png)


### HMMs can do do three primary tasks
- State Estimation P(S\O) - can be useful if you have prior info about what states mean and create the state probabilities yourself.

- Path Estimation - given observations, what is the most likely "state path"? Not useful in our case, and not even implemented here

- Maximum Likelihood Estimation P(O\λ) - learn the HMM parameters  λ  which maximize the probability of observations. This is the primary method we will use.

- **We will use Baum Welch algorithm**

### Baum-Welch algorithm

- The Baum-Welch algorithm is an iterative expectation-maximization (EM) algorithm that converges to a locally optimal solution from the initialization values.

- This is an EM algorithm for training the emission and transition probabilities of hidden Markov models in a fully automated way.

- It can be employed as long as a training set of annotated sequences is known, and provides a rigorous way to derive parameter values which are guaranteed to be at least locally optimal.

- Finding the parameters λ that maximize the likelihood of the observations
![image](https://user-images.githubusercontent.com/53213766/174874895-18d4a4a8-e8ef-416a-bd46-9c27c294edfa.png)
- The E-step thus consists of calculating these expectations for a fixed λ
![image](https://user-images.githubusercontent.com/53213766/174874938-4e56961d-4cb5-4412-a62d-ee372bcea15e.png)

### Results
- Time Series representation for banana audio (Amplitude vs Time domain)

![image](https://user-images.githubusercontent.com/53213766/174875403-63e66b60-4982-4112-a2b3-53dda294a408.png)

- Accuracy of the model
 
![image](https://user-images.githubusercontent.com/53213766/174875002-23669767-1961-4716-919c-a18bfa6e8090.png)

- Confusion matrix for the model

![image](https://user-images.githubusercontent.com/53213766/174875016-633832dd-96a9-47f4-ad77-898f0833f498.png)

### Conclusion & Future Scope
- During this project a system for isolated-word speech recognition was implemented and tested. The cross-validation results are good for a single speaker. 

- Two obvious extensions are better support for several speakers, and support for continuous speech. The first step towards the former would be more, and more robust, features. For the latter the simplest approach is probably to detect word boundaries and then proceed with an isolated-word 8 recognizer. 

##### Thank You :)
#### Sai Ganesh N
