# Machine Learning exam PhD
Little Machine Learning project for the PhD exam. PhD Student: Francesco Scala, Teacher: Jennifer Ngadiuba

## Repository content
The `ML_exam_PhD.ipynb` file is a Jupyter Notebook containing the project's code. The `data_dir` is a directory containing some saved data needed to show results without re-running the code for different numbers of qubits (see below).

## The problem

We want to apply Machine Learning techniques to classify quantum states possibly coming from an experiment. The main goal is to distinguish *random* quantum states (which can be seen as background noise) from states having a particular distribution (the ones coming from the experiment). Quantum states will be complex matrices produced by *quantum circuits* through `pennylane` Python library. In Sec. 1 this is treated as a binary classification problem, while in Sec. 2 we address a multi-class classification problem by adding an extra class (corresponding to results from another experiment).

In particular, in Sec. 1 we study the effect of the dataset size.
In fact, since quantum states of $n$ qubits live in a Hilbert space of dimension $d=2^n$ which is exponential in the number of qubits itself, one can see that a fixed dataset size leads to overfitting and poor performance of the model as the number of qubits increases.
For this reason, we will repeat the training procedure of a MLP with different datasets corresponding to different numbers of qubits ($n\in\{2,3,4,5\}$) for both the case with fixed (Sec 1.0) and exponential (Sec 1.1) dataset sizes. 

(We gathered the results of the different trainings in a single file and then we compare the results through their loss histories and ROC curves. One can skip directly to the *Multi-qubit data analysis* sections (1.1.3 and 1.2.3) load the data and see the results.)

While in Sec. 2 we complicate the classification task by adding data coming from different experiments (extra classes) to be distinguished one from the other and from noise. This is done for 5 qubits with exponentially big dataset (equally divided in 3 classes). We will see that the MLP (Sec. 2.1) employed in the previous section is able to perform well also in this case, but employing a CNN (Sec. 2.2) will improve the performance while reducing the number of parameters (from 80k to 30k).

### Table of content

  * 1 Binary Classification
    *  <br>
    
        * 1.0.1 Make binary dataset function
        * 1.0.2 Create binary dataset
    * 1.1 Fixed dimension dataset
        * 1.1.1 Build and train model
        * 1.1.2 Data analysis
        * 1.1.3 Multi-qubit data analysis
    * 1.2 Exponentially big dataset
        * 1.2.1 Build and train model
        * 1.2.2 Data analysis
        * 1.2.3 Multi-qubit data analysis
  * 2 Multiclass Classification
    *  <br>
    
        * 2.0.1 Build multiclass dataset function
        * 1.0.2 Create dataset
    * 2.1 MLP
        * 2.1.1 Build and train model
        * 2.1.2 Data analysis
    * 2.2 CNN
        * 2.2.1 Build and train model
        * 2.2.2 Data analysis

