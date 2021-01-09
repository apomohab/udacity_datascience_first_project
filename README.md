# Stackover flow data in year 2017.

### Based on the ( CRISP - DM ) Rules , we will make data analysis for Stackover Flow web site on 2017
**This project aims to analyze developers' data for a year 2017, with the aim of extracting the necessary data and information about the nature of work of developers and those interested in the field of programming and benefiting from the opinions of experts in the field**



# What is (CRISP - DM )

## Cross-industry standard process for data mining
**Cross-industry standard process for data mining, known as CRISP-DM ,  is an open standard process model that describes common approaches used by data mining experts. It is the most widely-used analytics model**

## CRISP-DM breaks the process of data mining into six major phases

<a href="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b9/CRISP-DM_Process_Diagram.png/639px-CRISP-DM_Process_Diagram.png/" rel="some text">![Foo](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b9/CRISP-DM_Process_Diagram.png/639px-CRISP-DM_Process_Diagram.png)</a>


* Business Understanding
* Data Understanding
* Data Preparation
* Modeling
* Evaluation
* Deployment


**The sequence of the phases is not strict and moving back and forth between different phases as it is always required. The arrows in the process diagram indicate the most important and frequent dependencies between phases. The outer circle in the diagram symbolizes the cyclic nature of data mining itself. A data mining process continues after a solution has been deployed. The lessons learned during the process can trigger new, often more focused business questions, and subsequent data mining processes will benefit from the experiences of previous ones.**



# Requirements to run this tutorial
**To follow this tutorial you need to have the following packages installed:**

- Python version  3.
- pandas latest version  http://pandas.pydata.org/ 
- numpy latest version http://www.numpy.org/
- matplotlib latest version http://matplotlib.org/
- seaborn https://seaborn.pydata.org/
- scikit-learn Machine Learning in Python https://scikit-learn.org/stable/



# Project Analysis Steps .

## we will look the data and apply the steps CRISP - DM

### Step 1 - 2 : Business understand & Data understand

**in this step we need to get answers for some questions from data like examples**

* how many the programmers contribute to open source projects in united state ?

* how many the gender of male have the Computer science or software engineering degree ?

* how many the ProgramHobby and what about the dataframe ?


## Question 1 :
* how many the programmers contribute to open source projects in united state ?

 **for answer this question we need to explore the columns  
 [ProgramHobby] and [Country] for check all options and get many programming 
 contribute to open source projects in united state**
 
 

    def pg_hobby():
    
    """
    for answer this question we need to explore the columns  
    [ProgramHobby] and [Country] for check all options and get many programming 
    contribute to open source projects in united state .
    """
    
    #count all types in the varibles ProgramHobby
    print(" The All Count  ProgramHobby  \n \n" + str(df['ProgramHobby'].value_counts()) + "\n\n")
    
    #count all types in the varibles Country
    print(" The All Count Countries  \n \n " + str(df['Country'].value_counts())  + "\n\n")
    
    #selected the data we need to get only based on the question .
    pg_contribute_op = df.loc[(df['ProgramHobby'] == 'Yes, I contribute to open source projects') & (df['Country'] == 'United States')]
    
    #Display The Answer
    print("the many programmers contribute to open source projects in united state is " + str(len(pg_contribute_op)))
    
    #Display the data frame .
    return pg_contribute_op.head(3)
    
     pg_hobby()




# Question 2. 
## how many the gender of male have the Computer science or software engineering degree ?




    def gender_degree():
    
    """
    for answer this question we need to explore the columns  
    [MajorUndergrad] and [Gender] for check all options and know  
    the gender type have a Computer science or software engineering degree.
    """
    
    #count all data in the varibles MajorUndergrad
    print(" The All Count the MajorUndergrad  \n \n" + str(df['MajorUndergrad'].value_counts()) + "\n\n")
    
    #count all types in the varibles Genter 
    print(" The All Count the Gender  \n \n " + str(df['Gender'].value_counts())  + "\n\n")
    
    #selected the data we need to get only based on the question .
    degree_male = df.loc[(df['MajorUndergrad'] == 'Computer science or software engineering') & (df['Gender'] == 'Male')]
    
    #Display The Answer
    print("many the gender of male have the Computer science or software engineering degree is " + str(len(degree_male)))
    
    #Display the data frame .
    return degree_male.head(3)
    
    
    #called function    
    gender_degree()
    


# Question 3.
**Provide a pandas series of the  ProgramHobby  values in the dataset along with the count of the number of individuals with each status. 
and make a bar chart of the proportion of individuals in each status**




    def ProgramHobby_Types():
    
    """
    for answer this question we need to explore the column 
    [ProgramHobby] and countt all types.
    """
    
    
    #count the programhobby varible and make bar chart 
    status_vals = df['ProgramHobby'].value_counts()
    
    #devision thee counts at the shape then make bar chart
    (status_vals/df.shape[0]).plot(kind="bar");
    
    #assign the title 
    plt.title("ProgramHobby values in the dataset ");


     #called function
     ProgramHobby_Types()
    


# step 3  : Prepare Data. 

 - in this step we will working around data and make cleaning data 
 - in this step we need to know some info same 
 
  * what is percent missing values in the varibles
  * what is varibles have more missing values
  * what is frequent values in the varibles
  * what is the best decesion for missing values
  * Assign the predicts varibles and Response varibles


        def Perecnt_Missing():
    
        '''
        we need to get the percent missing values 
        in all columns for see what is varibles 
        have more missing values.
        '''
    
        #select the missing values and get sum then 
        #multiplication * 100 then division at the len dataframe 
        percent_missing = df.isnull().sum() * 100 / len(df)
        missing_value_df = pd.DataFrame({'Column_name': df.columns,
                                 'percent_missing': percent_missing})
    
        #Display from 0 to 20 columns
        return missing_value_df[0:20]


        #called function
        Perecnt_Missing()






# Chose the predicts varibles inside list and check the missing values in this varibles
## then check the count values for know what is values more repeats

    def the_missing_in_predict():
    
    '''
    Missing Values :
    
    the first step in preparing data the "Missing Values" 
    In statistics, missing data, or missing values,
    occur when no data value is stored for the variable
    in an observation Missing data are a common occurrence and 
    can have a significant effect on the conclusions
    that can be drawn from the data.
    
    ---

    Predicted Varible :
    
    Predictor variable is the name given to an independent
    variable used in regression analyses The predictor 
    variable provides information on an associated dependent 
    variable regarding a particular outcome The term predictor
    variable arises from an area of applied mathematic that uses
    probability theory to estimate future occurrences of an event
    based on collected quantitative evidence.
    '''
    
 
    #in this code we will know how many percent the missing values in predict varibles 
    #create list have the Predicted Varible 
    predict_varibles  = df[['Professional' , 'MobileDeveloperType' , 'WebDeveloperType', 'YearsProgram']]
    #get the sum missing values and multiplication * 100 then division at the len dataframe
    percent_missing = predict_varibles.isnull().sum() * 100 / len(df)
    
    #Display
    print(percent_missing)
    

    '''
    after we know the percent of missing values 
    in the varibles in this step we will know 
    what is the most frequent values in
    predict varibles.
    
    '''
    
    #add the list predict varibles in teh loop
    #for not repeat the code more time 
    for column in predict_varibles:
        print("\n" + column)
        print(df[column].value_counts())
        
        
     #called function
     the_missing_in_predict()









# Take the decision for missing values  and assign the Predicts varibles and Response varible.



    def fillna_col(df):
    
    '''
    One of the best ways to working with missing values 
    is to replace the lead value with the most 
    frequently occurring value inside the variable
    used the function (fillna) but why Replace ?
    
    ---
    
    The presence of missing values in the data
    will greatly affect the model's expectations 
    at the end of the analysis Therefore,some 
    operations must be performed on those values.
    There are some common processes in dealing with 
    missing values and there are also some suggestions
    made by the analysis experts If the missing values 
    represent 5 % of the total data We will do some
    operations on it, such as replacing it with the 
    arithmetic mean or the median or with the most 
    frequent value of the variable, and if the missing
    values reach 90% we can clear those rows or replace 
    the missing values according to the importance of the data.
    
    
    ---
    
    After looking at the percentage of missing data
    within the variables, we will now replace the 
    missing values with the most frequent value 
    inside the variable by using a function (fillna)
    '''
    
    #(Professional developer) is the most frequent value 
    #inside the variable (Professional) So we will add to be 
    #Place of missing values
    df['Professional'].fillna('Professional developer' , inplace=True)
    
    #(Android) is the most frequent value 
    #inside the variable (MobileDeveloperType) So we will add to be 
    #Place of missing values
    df['MobileDeveloperType'].fillna('Android' , inplace=True)
    
    #(Full stack Web developer) is the most frequent value 
    #inside the variable (WebDeveloperType) So we will add to be 
    #Place of missing values
    df['WebDeveloperType'].fillna('Full stack Web developer' , inplace=True)
    
    #(20 or more years) is the most frequent value 
    #inside the variable (YearsProgram) So we will add to be 
    #Place of missing values
    df['YearsProgram'].fillna('20 or more years' , inplace=True)
    
    #select the predict varible in the list 
    predict_varibles = df[['Professional' , 'MobileDeveloperType' , 'WebDeveloperType', 'YearsProgram']]
    
    
    '''
    Tow : Convert The Predict Category Varible To Quantitative. 
    
    In science Machine learning, we use machine learning algorithms
    Those algorithms take the data that we will identify in the prediction
    and response variables and train the model on them so that it can predict
    more accurate values that are suitable for dependence But if the data for 
    those variables is text, we will convert them into digital data, between 0 and 1
    which is because machine learning algorithms  work on Quantitative data 
    so that they can predict more accurate values in the model
    
    ---
    
    get_dummies :
    
    the get_dummies is metthod used for Convert 
    categorical variable into dummy/indicator variables.
    
    Concat :
    
    Pandas concat() method is used to concatenate pandas
    objects such as DataFrames and Series.
    we use (concat) after used the method get_dummies
    for add the new varibles That was converted from  
    Category to Quantitative to DataFrame .
    
    '''
    
    #Convert the predict Category varibles to Quantitative 
    #used the method (get_dummies)
    df_new = pd.get_dummies(predict_varibles, dummy_na=False)
    
    #add the new varibles have a Quantitative data
    #to dataframe used method (Concat)
    df = pd.concat([df , df_new], axis=1)
    
    #we will delete the main varible have category data because we have 
    #now alternative varibles have  Quantitative data Converted from those variables
    #col_to_delete = df[['Professional' , 'MobileDeveloperType' , 'WebDeveloperType', 'YearsProgram']]
    #df.pop(col_to_delete)
    
    
    #here we will chek the missing valuesin colums still found or deleted
    percent_missing = predict_varibles.isnull().sum() * 100 / len(df)
    print("\n the missing values percent is \n \n " + str(percent_missing))
    

    '''
    Response Varible :
    
    Response variables are also known as dependent variables,
    y-variables, and outcome variables. Typically, you want to
    determine whether changes in the predictors are associated 
    with changes in the response.
    
    For example, in a plant growth study, the response variable
    is the amount of growth that occurs during the study. 
    The investigators want to determine how changes in the
    predictors are associated with changes in plant growth. 
    The predictors are the amount of fertilizer applied,
    the soil moisture, and the amount of sunlight.
    
    "Meet Jim"
    
    ---
    
    
    Imputing Missing Values:
    
    It is one of the common methods of dealing with missing
    values and refers to replacing the missing value with
    the arithmetic mean or median of the variables .

    '''
    
    #Display the mean response varible.
    Mean_Y = df['Salary'].mean()
    
    #Convert the missing values to the (mean)
    #used method (fillna)
    df['Salary'].fillna(Mean_Y, inplace=True)
    
    # validation the Respone varible have missing values
    if df['Salary'].isnull().any() == True:
        
        #show message if have any missing value
        print('Please Replace The Missing Values ')
        
    else:
        #if replace the missing value print the count values
        print("\n The Value Counts for Response Varible is  \n")
        print(df['Salary'].value_counts())
    
    
    '''
    After cleaning the data we will assign the 
    Predict varible and called (X) 
    and Response varible Called (y)
    '''
    
    #add global functon to predict varible for used out main method 
    global X
    
    #Assign the predict varible  called x
    X = df_new
    
    #add global functon to Response varible for used out main method 
    global y
    
    #Assign the Response varible called y
    y = df['Salary']
    
    #Validation from len the Response varible. 
    print('\n The len Response varible after replacing values is ' + str(len(y)))
    
    #validation of the len predicts varibles
    print("\n \n The len for predicts varibles is " + str((len(X)))  + " \n \n")
    
    #Display head the new Quantitative predicts varibles  
    return (X.head())


    #called function
    fillna_col(df)


# Step 4 - Data Modeling .
**in this step we will work in machine learning step**


     def data_modeling():
    
    '''
    in this section we will building the model
    for predict the salary based on the 
    Predict data .
    '''

    #split data 
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = .30, random_state=42) 

    # Instantiate Model
    model = LinearRegression(normalize=True) 

     #Fit Model
     model.fit(X_train, y_train) 

     #Predict and score the model
    predict = model.predict(X_test) 

    #Display Predict
    print(predict)

    #called function
    data_modeling()




# Step 5 - Evaluate Results.

    def evaluated():
    
    '''
    this is final step in analysis 
    we will evaluated Results model
    used by Accuricy algorithms
    '''
    
    #Accuracy Model used Algorithm (Mean Squared Error)
    print("The mean squared score for the model using only quantitative variables was {} on {} values.".format(mean_squared_error(y_test, predict), len(y_test)))

     #Accuracy Model used Algorithm (r-squared Error)
    print("The r-squared score for the model using only quantitative variables was {} on {} values.".format(r2_score(y_test, predict), len(y_test)))

    
    evaluated()


# The Results Predict model 

#### The mean squared score for the model using only quantitative variables was 1.0002248107407395e+29 on 15418 values.

#### The r-squared score for the model using only quantitative variables was -2.48560182584156e+20 on 15418 values.


# Conclusion

**This Project is found in udacity Data Science Nano Degre program at this link**
**https://www.udacity.com/course/data-scientist-nanodegree--nd025**


# For Downlaod all data files for stackoverflow  
**https://insights.stackoverflow.com/survey**




# for see the explain project in blog medium in this link 
**https://sa3ed.medium.com/stack-overflow-data-in-2017-35230234665d**

**Thank you for review my project**

**Best Wishes**

**Authoring by**

**Saeede Shaban**
