# -Probability_Density_Functions_using_data
Learning Probability Density Functions using Data Only
1. Methodology

Data Collection → Data Pre-processing → Non-Linear Transformation →
GAN Training → Sample Generation → PDF Approximation → Result Analysis

2. Dataset Information

Dataset Name: India Air Quality Dataset
Source: Kaggle
Dataset Link: https://www.kaggle.com/datasets/shrutibhargava94/india-air-quality-data

Feature Used: NO₂ concentration

The dataset contains air quality measurements collected across multiple Indian cities.
The NO₂ feature is selected as the input variable for learning the probability density function.

3. Objective

The objective of this assignment is to learn an unknown probability density function of a transformed random variable using only data samples. No analytical or parametric form of the probability density function is assumed. A Generative Adversarial Network (GAN) is used to implicitly learn the distribution.

4. Mathematical Formulation
Non-Linear Transformation

Each NO₂ value 
𝑥
x is transformed into 
𝑧
z using the roll-number-parameterized non-linear function:

𝑧
=
𝑥
+
𝑎
𝑟
sin
⁡
(
𝑏
𝑟
𝑥
)
z=x+a
r
	​

sin(b
r
	​

x)

where

𝑎
𝑟
=
0.5
×
(
𝑟
 
m
o
d
 
7
)
a
r
	​

=0.5×(rmod7)
𝑏
𝑟
=
0.3
×
(
𝑟
 
m
o
d
 
5
+
1
)
b
r
	​

=0.3×(rmod5+1)

and 
𝑟
r is the university roll number.

Transformation Parameters

For the given university roll number:

University Roll Number (r): 102317146

𝑎
𝑟
=
3.0
a
r
	​

=3.0

𝑏
𝑟
=
0.6
b
r
	​

=0.6

GAN-Based Density Learning

Real samples: 
𝑧
z

Fake samples: 
𝑧
𝑓
=
𝐺
(
𝜖
)
z
f
	​

=G(ϵ), where 
𝜖
∼
𝑁
(
0
,
1
)
ϵ∼N(0,1)

The generator implicitly models the probability distribution of 
𝑧
z

No parametric probability density function is assumed

5. GAN Architecture Description
Generator Network

Fully connected neural network

Input: One-dimensional noise sampled from a standard normal distribution

Output: Generated samples of the transformed variable 
𝑧
z

Discriminator Network

Fully connected neural network

Input: Real or generated samples

Output: Probability of the input sample being real

The generator and discriminator are trained adversarially until the generator produces samples that resemble the real transformed data.

6. PDF Approximation from Generator Samples

After training the GAN:

A large number of samples are generated using the generator

Kernel Density Estimation (KDE) is applied to the generated samples

The estimated density represents the learned probability density function of 
𝑧
z

7. Input / Output
Input

NO₂ concentration values from the air quality dataset

Output

Transformed variable 
𝑧
z

Generated samples from the GAN

Estimated probability density function 
𝑝
(
𝑧
)
p(z)

8. Result Graph

The figure below shows:

Histogram of real transformed samples 
𝑧
z

KDE-based probability density function estimated from GAN-generated samples

PDF Estimation Plot
PDF Estimation using GAN Generated Samples

9. Observations
Mode Coverage

The generator captures the dominant mode of the transformed variable.

Training Stability

Training remains stable due to normalization of data and the use of a simple GAN architecture.

Quality of Generated Distribution

The estimated probability density function closely follows the empirical distribution of the real samples, with minor deviations in the tails.

10. Conclusion

This assignment demonstrates that Generative Adversarial Networks can be used to learn an unknown probability density function directly from data samples. The approach avoids assuming any analytical form of the distribution and provides a purely data-driven solution for density estimation.

11. Tools & Technologies Used

Google Colab

Python

NumPy

Pandas

TensorFlow / Keras

Matplotlib

Scikit-learn
