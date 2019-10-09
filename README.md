# Analysis_Of_Pruning_Techniques

This repositry contains code analysing two methods of pruning - *Model Pruning* and *Unit Pruning* on a large dense network trained on MNIST.

### Prerequisites


```
pip3 install -r requirements.txt
```

### Run notebook on Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/gowtham1997/Analysis_Of_Pruning_Techniques/blob/master/Network_Pruning.ipynb)

### Analysis / Results

- *Weight pruning* outperforms *Unit pruning* when we are measuring model accuracy.

- In case of *Weight pruning* the performance only starts decreasing after 90% sparsity, while in the case of *Unit pruning* the decline happens much earlier starting from 70% sparsity.

- At 99% sparsity, both methods predict at random(accuracy of 10 % for classifying 10 classes)

- One of the reasons why the model's performance is not hurt even after 80% weight pruning could be that most of the values in the trained model are around 0(as seen from the plot). Perhaps we can postulate that only 10 - 15 % of the weights contribute to the task.

- The major benefit of *Unit pruning* over *Weight pruning* is the computational speed. Since we are removing neurons(deleting the smallest k% according to their L2-norm) in *Unit pruning*, the model parameters reduce drastically and this enhances speed.

- Sparse linear algebra operations enhance the speed of the model in case of *Weight pruning* but only when the sparsity is significant(above 80% in this task).


