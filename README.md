# Social-Media-Usage-and-Mental-Health

The project simply tried to find the relationship between social meadia use and mental health status of social media users.

## Research Questions
Research Questions:
- What is the relationship between mental health and social media use?
- What are the common types of people that uses social media and show signs of mental health problems?
- Can intensity of social media use be an indicator to mental health problems?

## Dataset
This dataset was originally collected for a data science and machine learning project that aimed at investigating the potential correlation between the amount of time an individual spends on social media and the impact it has on their mental health. There is no information on when and how the data is collected. 
The original dataset can be found on Kaggle through this link: https://www.kaggle.com/datasets/souvikahmed071/social-media-and-mental-health

## First Glance to Data
The dataset includes 21 columns and 481 non-null rows.
The column names are: 'Timestamp', '1. What is your age?', '2. Gender', '3. Relationship Status', '4. Occupation Status', '5. What type of organizations are you affiliated with?', '6. Do you use social media?', '7. What social media platforms do you commonly use?', '8. What is the average time you spend on social media every day?', '9. How often do you find yourself using Social media without a specific purpose?', '10. How often do you get distracted by Social media when you are busy doing something?', '11. Do you feel restless if you haven't used Social media in a while?', '12. On a scale of 1 to 5, how easily distracted are you?', '13. On a scale of 1 to 5, how much are you bothered by worries?', '14. Do you find it difficult to concentrate on things?', '15. On a scale of 1-5, how often do you compare yourself to other successful people through the use of social media?', '16. Following the previous question, how do you feel about these comparisons, generally speaking?', '17. How often do you look to seek validation from features of social media?', '18. How often do you feel depressed or down?', '19. On a scale of 1 to 5, how frequently does your interest in daily activities fluctuate?', '20. On a scale of 1 to 5, how often do you face issues regarding sleep?'.

I first cleaned the data from useless variables. Then recoded gender and average time on social media variable to numeric variables. Also I created new 4 variables called ADHD, Anxiety, Self-Esteem, Depression out of 12 variables.
ADHD contains questions: How often do you find yourself using Social media without a specific purpose?, How often do you get distracted by Social media when you are busy doing something?, On a scale of 1 to 5, how easily distracted are you?, On a scale of 1 to 5, how easily distracted are you?
Anxiety contains questions: Do you feel restless if you haven't used Social media in a while?, On a scale of 1 to 5, how much are you bothered by worries?
Self-Exteem contains questions: On a scale of 1-5, how often do you compare yourself to other successful people through the use of social media?, Following the previous question, how do you feel about these comparisons, generally speaking?, How often do you look to seek validation from features of social media?
Depression contains questions:  How often do you feel depressed or down?, On a scale of 1 to 5, how frequently does your interest in daily activities fluctuate?, On a scale of 1 to 5, how often do you face issues regarding sleep?

I have created a new variable called 'mental_health_prob_score' that contains ADHD, Anxiety, Self-Esteem, and Depression scores.
I have finally created a binary variable called 'needs_counselling' that is based on 'mental_health_prob_score'. If score is equal or higher than 42, it is coded as 1, else 0. The reason I choose 42 is if a person answers all of the questions as neutral, the socre would be 36. If answers all of them as 4, it would be 48. I choose the number in between, which is 42.

## Results

After exploratory data analysis, I did run k-means clustering based on average social media use time and mental_health_prob_score variables. According to elbow method, there are 3 ideal clusters. There groups are called 'natives', 'exotic birds', and 'regular users'
<img width="944" alt="image" src="https://github.com/zeybus/Social-Media-Usage-and-Mental-Health/assets/113775433/1af51b33-36a4-4c19-ac13-5f73dce071d8">

After clustering, I have also run logistic regression based on average daily social media use, age, gender, adhd, anxiety, self-esteem, depression, and needs_counselling variables. The dependent variable is 'needs_counselling'. The variable adhd is removed from the analysis, as it might cause collinearity; it has high correlation to both dependent variable and anxiety variable. Finally,  <b> the accuracy of logistic regression is 90% </b>, meaning people with high social media use and have symtoms of diverse mental health issues based on usage of social media behaviors needs counselling. Below, you can see correlation table, and confusion matrix.

![image](https://github.com/zeybus/Social-Media-Usage-and-Mental-Health/assets/113775433/96082338-f5b7-42b7-bf5f-ab9c579309ce)

<img width="70" alt="image" src="https://github.com/zeybus/Social-Media-Usage-and-Mental-Health/assets/113775433/a88561eb-1cb6-41ed-be7e-35df8bcebe1f">




