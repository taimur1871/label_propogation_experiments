# Label Propogation Experiments

This repo contains notebook inspired by label propogation example from sklearn.
The notebook also plays with various samples sizes and compares the results on the predicted labels.

## Results

For these tests the unlabeled set was 20% of the total samples. It is quite high especially for smaller size datasets but it did reveal some interesting results. The link below shows scores for precision and recall for various sample sizes.

Obviously the smaller samples had very low accuracy.
* 10 samples 0 F1 score (the model is just guessing)
* 100 samples 0.56 F1 score (still guessing but accurate at least half the time)
* 250 samples 0.90 F1 score (much imporved model)
* 500 samples 0.93 F1 score (performance plateauing)

Based on the above observations it can be seen that performance increases rapidly as number of training samples are increased upto a point. Also to get fairly good performance the number of samples do not need to be very high as long as the starting categories are well defined.

In case of 10 and 100 samples the starting categories did not have any representative samples or very low numbers in certain categories so the model had no way to learn and propogate those samples.

This can be seen in the predictions, the first model predits either 0 or 4 presumably because it did not have any 0 samples so it assumes any category that it is unable to identify must belong to 0, and 4 becasue it seems like the most readily identifiable or applicable label (can be applied to 1, 7 for example.

At 100 samples some categories have more samples than others. Intresting observation in this case is that the model does not accurately predict any of the labels in the categories that are over represented. For example 8 has most samples but it constantly mislabels it as 9 or 4.

At 250 samples the predcitions start getting better. However, 8, 9 and 4 still seem to cause problems.

At 500 samples the performance improves marginally in terms of F1 score but perfromance in identifying 9 improves. 8 still proves challenging.

Overall the number that seems to prove most challenging is 8, it is possible to confuse it with 3, 8, 9 or even 1 depending on the resoltion and handwriting style.
