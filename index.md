# Missing data and similarity

Tutoring systems are computer systems which purpose is to teach its users (students) some knowledge or skill. The key part of learning is solving questions. I was working with dataset from tutoring system Umíme česky that provides thousands of such questions.

For management of the questions, I wanted to display them in some way that can be naturally interpreted. Following text describes one way of doing so.

## Projection of questions

![Sample projection](sample_projection_diagram.svg)

Each dot in the image represents one question, and its proximity to others represents how similar they are. E.g., question "b\_ografie" is quite similar to "b\_olog", but it is not similar to "zb\_tek".

For this I choose to utilize correctness of answers from users. We consider questions to be similar when they are answered similarly by users. But I want to know if similarity of questions can also be affected by structure of system.

## Similarity pipeline

![Similarity pipeline](pipeline_diagram.svg)

First I take data about user performance and compare each pair of questions using Pearson correlation coefficient. This yelds us square matrix containing similarity of all pairs of questions. After that I apply PCA to reduce this similarity matrix into a 2D projection. Projection is representation of questions useful for visualizations for end users. Like image I showed.

## Pattern of missing data

Not all users answer all of the questions. On the contrary, performance matrix is relatively sparse. However, missing values are not distributed randomly, but they form a pattern.

My question was whether this pattern can affect similarity of questions and therefore projections.

Questions in each topic of the system are divided into up to three levels. The difficulty of the levels raises. Users in the system usually do not solve all of the levels. Less experienced users usually solve only first or first two levels. But, more experienced users solve only higher levels.

## Conclusion

![Simulated data with missing answers](simulated_missing.png)

I simulated virtual to users to generate data with missing answers to verify whether this factor alone can cause such regularity. Image shows projection of simulated questions. Colors of points represents their level (purple - first, yellow - second, and green - third). It is visible, that pattern of missing answers can affect similarity of questions.

## Continue reading

I focused on this topic in my [bachelor's thesis](http://ienze.me/tmsei_thesis/) and I found that more such factors exists. If you are interested you can continue reading about them there.
