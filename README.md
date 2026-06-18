The steps to do end-to-end project:
1. Data Loading ✅
2. Data Understanding ✅
3. Data Cleaning ✅
4. Exploratory Data Analysis ✅
5. Feature Engineering ✅
6. Train Model ✅
7. Save model with joblib ✅
8. Fastapi Wrapping and Dockerizing
9. Deploying


I am doing my first real end-to-end project. Most people quit after doing some steps and cannot reach to end of the pipeline. 
I got real data from Kaggle called Student Lifestyle and Stress Dataset. 

1, 2. Data Loading and Understanding
Initially, I got dataset and downloaded, and grasp of idea what is under the hood.

3.Data Cleaning
Next step is about cleaning data, which is the most percentage of work lies here. First, i used some methods to get what kinda columsn and shape that data has:
.info(), .describe(), .shape(), .size(), .sample(). I saw duplicates using df.duplicated().sum(), then I dropped using df.drop_duplicates() to prevent from messiness.
Next, I saw null values for columns and got their percentage to act whether to drop or fill. All columns have about 5 % missed null data. I preferred to fill them as
they are too small percentage of the data. df.fillna(mode) i used this for categorical and for numerical i used median to fill.

4. EDA
In Exploratory Data Analysis, I got 6 hypothesis and write them to my notepad, then i focused on plotting to draw conclusions from it.
Each varibale checked against the target columns using appropriate plots(boxplot, violinplot, countplot, scatterplot and so on) and followed by exact group statistics (median, mean) to confirm visual trends. A correlation heatmap across all numeric features was used as a final cross-check.
<img width="713" height="507" alt="image" src="https://github.com/user-attachments/assets/514dba0e-0183-495a-8a23-859f7682a104" />

exam_pressure --> Higher pressure → higher stress |
student_type --> working_student > college > school |
study_hours --> Slightly higher in stressed students |
sleep_hours --> Equal medians, more variance in stressed group |
family_support --> Equal medians, minor mean differenceWeak |
social_media_hours --> No meaningful difference |
attendance --> No relationship with target or with exam_pressure |

# Conclusions
exam_pressure and student_type are the dominant signals for predicting stress_level. study_hours adds secondary value. sleep_hours, family_support, social_media_hours, and attendance show weak-to-negligible standalone effects and may be candidates for removal or for combination into interaction features in later modeling steps.

5. Feature Engineering
First, I turned categorical columns into numerical cols using get_dummies() method of pandas as machine cannot read letters, it only sees numbers that is why i did that job. Then, I created some engineered features, like study_sleep_ratio, low_sleep = sleep<5 and so on

6. Model training
For training model, I created steps to do my work:
  0. An end-to-end Scikit-learn workflow
  1. Getting the data ready
  2. Choose the right model
  3. Fit the model/Algorithm and use it to make predictions about our data
  4. Evaluate a model
  5. Improve model
  6. Save and Load a trained model
  7. Putting it all together!
Initally, i get the ready data i ve cleaned and I chose Classification algorithm RandomForestClassifier for my project. Then, i splitted data into to parts: 80/20 for training and testing data, respectively and predicted data. I used classification_report, confusion_matrix and accuracy score for evaluation. Accuracy score was about 82%. This is my firt end-to-end project, so i think this is very good, and I will try to apply different algorithms and ways to improve accuracy while learning more. To improve the model, I tried different estimators like with for loop, all good ones are about 82%. So, then I saved model using joblib.dump() and loading is with joblib.load().
So, all end-to-end project is done. So, I am very happy to finish it.
