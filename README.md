Download Link: https://assignmentchef.com/product/solved-csc411-assignment-4-alexnet
<br>
<ol>

 <li><strong> AlexNet </strong>For this question, you will first read the following paper:</li>

 <li>Krizhevsky, I. Sutskever, and G. E. Hinton. ImageNet classification with deep convolutional neural networks. In Advances in Neural Information Processing Systems (NIPS), 2012.</li>

</ol>

<a href="http://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks">http://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks</a>

This is a highly influential paper (over 45,000 citations on Google Scholar!) because it was one of the first papers to demonstrate impressive performance for a neural network on a modern computer vision benchmark. It generated lots of excitement both in academia and in the tech industry. The architecture presented in this paper widely used today, and is known as “AlexNet”, after the first author. Reading this paper will also help you review a lot of the important concepts from this class.

<ul>

 <li><strong> </strong>They use a conv net architecture which has five convolution layers and three fully connected layers (one of which is the output layer). Your job is to count the number of units, the number of weights, and the number of connections in each layer. I.e., you should complete the following table:</li>

</ul>

<table width="0">

 <tbody>

  <tr>

   <td width="172"></td>

   <td width="83"><strong># Units</strong></td>

   <td width="94"><strong># Weights</strong></td>

   <td width="117"><strong># Connections</strong></td>

  </tr>

  <tr>

   <td width="172">Convolution Layer 1Convolution Layer 2Convolution Layer 3Convolution Layer 4Convolution Layer 5 Fully Connected Layer 1Fully Connected Layer 2 Output Layer</td>

   <td width="83"></td>

   <td width="94"></td>

   <td width="117"></td>

  </tr>

 </tbody>

</table>

You can ignore the pooling layers when doing these calculations, i.e. you don’t need to consider the units in the pooling layers or the connections between convolution and pooling layers. You can also ignore the biases. Note that the paper gives you the answers for the numbers of units in the caption to Figure 2. Therefore, we won’t mark the column for units, though you would benefit from trying to work it out yourself.

When counting the number of connections, we’ll adopt the convention that when the input to a convolution layer is zero-padded, the connections to the dummy zero values count towards the total. (This is the most convenient way to do it, since it means the number of incoming connections is the same for each unit in a given layer.)

<ul>

 <li><strong> </strong>Now suppose you’re working at a software company and want to use an architecture similar to AlexNet in a product. Your project manager gives you some additional instructions; for each of the following scenarios, based on your answers to Part 1, suggest a change to the architecture which will help achieve the desired objective. I.e., modify the sizes of one or more layers. (These scenarios are independent.)</li>

</ul>

<ol>

 <li>You want to reduce the memory usage at test time so that the network can be run on a cell phone; this requires reducing the number of parameters for the network. ii. Your network will need to make very rapid predictions at test time. You want to reduce the number of connections, since there is approximately one add-multiply operation per connection.</li>

</ol>

<ol start="2">

 <li><strong> Gaussian Na¨ıve Bayes. </strong>In this question, you will derive the maximum likelihood estimates for Gaussian Na¨ıve Bayes, which is just like the na¨ıve Bayes model from lecture, except that the features are continuous, and the conditional distribution of each feature given the class is (univariate) Gaussian rather than Bernoulli. Start with the following generative model for a discrete class label <em>y </em>∈ (1<em>,</em>2<em>,…,k</em>) and a real valued vector of <em>d </em>features <strong>x </strong>=</li>

</ol>

(<em>x</em><sub>1</sub><em>,x</em><sub>2</sub><em>,…,x<sub>d</sub></em>): <em>p</em>(<em>y </em>= <em>k</em>) = <em>α<sub>k                                                  </sub></em>(1)

<em>/</em>

where <em>α<sub>k </sub></em>is the prior on class <em>k</em>, <em>σ<sub>i</sub></em><sup>2 </sup>are the variances for each feature, which are shared between all classes, and <em>µ<sub>ki </sub></em>is the mean of the feature <em>i </em>conditioned on class <em>k</em>. We write <em>α </em>to represent the vector with elements <em>α<sub>k </sub></em>and similarly <em>σ </em>is the vector of variances. The matrix of class means is written <em>µ </em>where the <em>k</em>th row of <em>µ </em>is the mean for class <em>k</em>.

<ul>

 <li>Use Bayes’ rule to derive an expression for <em>p</em>(<em>y </em>= <em>k</em>|<strong>x</strong><em>,</em><em>µ,</em><em>σ</em>). <em>Hint: Use the law of total probability to derive an expression for p</em>(<strong>x</strong>|<em>µ,</em><em>σ</em>)<em>.</em></li>

 <li><strong> </strong>Write down an expression for the negative likelihood function (NLL)</li>

</ul>

<em>`</em>(<em>θ</em>;<em>D</em>) = −log<em>p</em>(<em>y</em>(1)<em>,</em><strong>x</strong>(1)<em>,y</em>(2)<em>,</em><strong>x</strong>(2)<em>,</em>··· <em>,y</em>(<em>N</em>)<em>,</em><strong>x</strong>(<em>N</em>)|<em>θ</em>)                                        (3)

of a particular dataset <em>D </em>= {(<em>y</em><sup>(1)</sup><em>,</em><strong>x</strong><sup>(1)</sup>)<em>,</em>(<em>y</em><sup>(2)</sup><em>,</em><strong>x</strong><sup>(2)</sup>)<em>,</em>··· <em>,</em>(<em>y</em><sup>(<em>N</em>)</sup><em>,</em><strong>x</strong><sup>(<em>N</em>)</sup>)} with parameters <em>θ </em>= {<em>α,</em><em>µ,</em><em>σ</em>}. (Assume the data are i.i.d.)

<ul>

 <li>Take partial derivatives of the likelihood with respect to each of the parameters <em>µ<sub>ki </sub></em>and with respect to the shared variances <em>σ<sub>i</sub></em><sup>2</sup>. Based on this, find the maximum likelihood estimates for <em>µ </em>and <em>σ</em>. You may assume that each class appears at least once in the dataset.</li>

 <li><strong> </strong>Show that the MLE for <em>α<sub>k </sub></em>is given by the following equation:</li>

</ul>

]                                                              (4)

You may assume that each class appears at least once. You will find it helpful to read about Lagrange multipliers<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>.

<a href="#_ftnref1" name="_ftn1">[1]</a> <a href="https://en.wikipedia.org/wiki/Lagrange_multiplier">https://en.wikipedia.org/wiki/Lagrange_multiplier</a>