# cifar10 with CNN

* Download final outcomes (extracted model1~5 and charts) [here](https://drive.google.com/drive/folders/1uJK7ztqqZPOjRRbhCTbxzJhha-H4ns2h?usp=sharing). <br><br>
<b> Model 1: Basic CNN </b>

* Structure: <br>
![Screen Shot 2021-06-28 at 5 57 39 PM](https://user-images.githubusercontent.com/67300266/123609147-60488400-d83a-11eb-9699-c6100a82eacd.png)
* Validation accuracy and Validation loss: <br>
![model1](https://user-images.githubusercontent.com/67300266/123609206-6d657300-d83a-11eb-9e4c-8744a5cd395a.png)
* Feedback: Model 1 is overfitted.
* Plan for model 2 and 3: Try out widely used methods (Dropout and Batch normalisation) to prevent overfitting.

<b> Model 2: CNN with Dropout </b>
* Structure: <br>
![Screen Shot 2021-06-28 at 5 58 52 PM](https://user-images.githubusercontent.com/67300266/123609330-8706ba80-d83a-11eb-8030-2480f4c5ef22.png)
* Validation accuracy and Validation loss: <br>
![model2](https://user-images.githubusercontent.com/67300266/123609365-8ec65f00-d83a-11eb-9303-b3f904545fb7.png)
* Feedback: Dropout contributes to avoid overfitting.
* Plan for model 3: Try out Batch normalisation and compare the result with the performance of model 2.

<b> Model 3: CNN with Dropout and Batch Normalisation </b>
* Structure: <br>
![Screen Shot 2021-06-28 at 6 00 04 PM](https://user-images.githubusercontent.com/67300266/123609535-b289a500-d83a-11eb-9757-ba3fe25ac339.png)
* Validation accuracy and Validation loss: <br>
![model3](https://user-images.githubusercontent.com/67300266/123609580-bddcd080-d83a-11eb-9db7-726d064b17e5.png)
* Feedback: Each model performance is similar to each other => Overfitting issue is almost resolved.
* Plan for model 4: Add data augmentation to increase accuracy.

<b> Model 4: Model 3 after Data Augmentation </b>
* Structure: <br>
![Screen Shot 2021-06-28 at 6 06 08 PM](https://user-images.githubusercontent.com/67300266/123610410-8884b280-d83b-11eb-83f2-c6331be70608.png)
* Validation accuracy and Validation loss: <br>
![model4](https://user-images.githubusercontent.com/67300266/123610703-cb468a80-d83b-11eb-86b8-75dfd54fd35c.png)
* Feedback: In general, train accuracies are higher than validation accuracy, but opposite outcome is shown in model 4 outcomes. <br>
There are 2 possible reasons for this: <br>
Premise 1: Data augmentation has only been applied for train data, which means validation data consists of easier (original) examples. <br>
Premise 2: Regardless of Data augmentation, validation data consists of easier examples by chance. <br>
Before we can defense of premise 1, it should be clarified that there is no problem with data split.
* Plan for model 5: Split the data again to check if premise 2 is valid.

<b> Model 5: Changed np.random.seed + Data augmentation </b>
![model5](https://user-images.githubusercontent.com/67300266/123612729-c71b6c80-d83d-11eb-837f-091019343a4a.png)
* Feedback: Compared to model 4, there's no big difference in the gap for both Losses and Accuracies.
# Conclusion
* As the basic CNN model (= model 1) keeps overfitting, dropout and BN (Batch normalisation) have been applied to avoid the issue. <br>
* For model 4, data augmentation is added to increase validation accuracy. <br>
* As we can see in model 4 outcomes, the validation loss is less than train's. <br>
* For model 5, np.random.seed value is changed to check if there's an issue with data split. <br>
* As we can see there is no dramatic difference for model 5, it can be concluded that the image examples for train were relatively harder than for validation as a result of data augmentation.

# References
* [Basic example of cifar10 and CNN from Kaggle](https://www.kaggle.com/roblexnana/cifar10-with-cnn-for-beginer)
* [Batch Normalisation](https://sonsnotation.blogspot.com/2020/11/8-normalization.html)
* [Dropout1](https://jjeongil.tistory.com/578)
* [Dropout2](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=laonple&logNo=220542170499)
* [Early stopping](https://www.tensorflow.org/api_docs/python/tf/keras/callbacks/EarlyStopping)
* [Greater validation accuracy than train accuracy](https://stackoverflow.com/questions/48845354/why-is-validation-accuracy-higher-than-training-accuracy-when-applying-data-augm)
* [Image Augmentation](http://machinelearningkorea.com/2019/05/19/image-augmentation-%EC%9D%84-%EC%9D%B4%EC%9A%A9%ED%95%98%EC%97%AC-%ED%9B%88%EB%A0%A8%EC%9A%A9-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EB%8A%98%EB%A6%AC%EA%B8%B0-%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EC%B9%98%ED%8A%B8/)
* [Paper for Dropout](https://www.cs.toronto.edu/~hinton/absps/JMLRdropout.pdf)


