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

I am doing my first real end-to-end project. Most people quit after doing some steps and cannot reach to the end of the pipeline. 
I got real data from Kaggle called Student Lifestyle and Stress Dataset. 

### 1, 2. Data Loading and Understanding
Initially, I got the dataset, downloaded it, and got a grasp of the idea of what is under the hood.

### 3. Data Cleaning
The next step is about cleaning data, which is where the highest percentage of work lies. First, I used some methods to see what kind of columns and shape that data has:
`.info()`, `.describe()`, `.shape()`, `.size()`, `.sample()`. I saw duplicates using `df.duplicated().sum()`, then I dropped them using `df.drop_duplicates()` to prevent messiness.

Next, I saw null values for columns and got their percentage to decide whether to drop or fill. All columns have about 5% missing null data. I preferred to fill them as they are a very small percentage of the data. I used `df.fillna(mode)` for categorical data, and for numerical data, I used the median to fill.

### 4. EDA
In Exploratory Data Analysis, I came up with 6 hypotheses and wrote them in my notepad, then I focused on plotting to draw conclusions from them.
Each variable was checked against the target columns using appropriate plots (`boxplot`, `violinplot`, `countplot`, `scatterplot`, and so on) and followed by exact group statistics (median, mean) to confirm visual trends. A correlation heatmap across all numeric features was used as a final cross-check.

<img width="713" height="507" alt="image" src="https://github.com/user-attachments/assets/514dba0e-0183-495a-8a23-859f7682a104" />

* **exam_pressure** --> Higher pressure → higher stress
* **student_type** --> working_student > college > school
* **study_hours** --> Slightly higher in stressed students
* **sleep_hours** --> Equal medians, more variance in stressed group
* **family_support** --> Equal medians, minor mean difference (Weak)
* **social_media_hours** --> No meaningful difference
* **attendance** --> No relationship with target or with exam_pressure

#### Conclusions
`exam_pressure` and `student_type` are the dominant signals for predicting `stress_level`. `study_hours` adds secondary value. `sleep_hours`, `family_support`, `social_media_hours`, and `attendance` show weak-to-negligible standalone effects and may be candidates for removal or for combination into interaction features in later modeling steps.

### 5. Feature Engineering
First, I turned categorical columns into numerical columns using the `get_dummies()` method of pandas, as a machine cannot read letters and only sees numbers—that is why I did that job. Then, I created some engineered features, like `study_sleep_ratio`, `low_sleep` = `sleep < 5`, and so on.

### 6. Model training
For training the model, I created steps to do my work:
* An end-to-end Scikit-learn workflow
* Getting the data ready
* Choose the right model
* Fit the model/Algorithm and use it to make predictions about our data
* Evaluate a model
* Improve model
* Save and Load a trained model
* Putting it all together!

Initially, I got the ready data I've cleaned and I chose the classification algorithm `RandomForestClassifier` for my project. Then, I split the data into two parts: 80/20 for training and testing data, respectively, and predicted data. I used `classification_report`, `confusion_matrix`, and accuracy score for evaluation. The accuracy score was about 82%. This is my first end-to-end project, so I think this is very good, and I will try to apply different algorithms and ways to improve accuracy while learning more. To improve the model, I tried different estimators using a for loop; all the good ones are about 82%. So, then I saved the model using `joblib.dump()` and loading is done with `joblib.load()`.

So, all the end-to-end project is done. So, I am very happy to finish it.
