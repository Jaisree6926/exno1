# Exno:1

Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output

# Data cleaning process


    import pandas as pd
    df=pd.read_csv("/content/SAMPLEIDS.csv")
    df

![Screenshot (162)](https://github.com/user-attachments/assets/8a66f221-fb3b-4130-9965-5d6235ab1e39)



    df.head()

![image](https://github.com/user-attachments/assets/eb85f11f-7a25-4386-af95-9897e13ac3e0)



    df.tail(5)

![image](https://github.com/user-attachments/assets/91480476-7090-4d29-97e4-0e07d6a25438)



    df.isnull()

![image](https://github.com/user-attachments/assets/ac23b0d5-fb49-4e34-867f-125892ea37c5)



    df.notnull()

![image](https://github.com/user-attachments/assets/b2cf23c4-df6b-4453-bca4-84b492fcb026)



    df.dropna(axis=0)

![image](https://github.com/user-attachments/assets/f34392ff-dff2-4954-9597-d0247031653c)



    df.dropna(axis=1)

![image](https://github.com/user-attachments/assets/7e1478dc-bde7-45de-ae3b-bd9b3f643c7f)



    df.fillna(0)

![image](https://github.com/user-attachments/assets/39f84c37-b4f8-4cc7-8034-77d16797f369)



    print(df.shape)

![image](https://github.com/user-attachments/assets/6b6c6d3c-ddf9-4cd3-a54c-575aece38d1b)



# IQR:

    import pandas as pd
    import seaborn as sns
    ir=pd.read_csv('/content/iris.csv')
    ir

![image](https://github.com/user-attachments/assets/f67b3a09-f274-4780-a37f-80943c5ec2e6)



    ir.describe()

![image](https://github.com/user-attachments/assets/b616bd03-9500-4a06-a89f-8b4e0f9b47b3)



    sns.boxplot(x='sepal_width',data=ir)

![image](https://github.com/user-attachments/assets/2bdf044a-4ad1-4904-abe2-4bef781f0b0c)



    c1=ir.sepal_width.quantile(0.25)
    c3=ir.sepal_width.quantile(0.75)
    iq=c3-c1
    print(c3)

![image](https://github.com/user-attachments/assets/9363cea0-382d-4b2e-af91-dd96ef413dac)



     rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
     rid['sepal_width']

![image](https://github.com/user-attachments/assets/287a3693-fee9-4ace-b14e-46d52df1aeec)



    delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
    delid

![image](https://github.com/user-attachments/assets/44234da0-e431-45a4-909a-d4011aebfbb1)



    sns.boxplot(x='sepal_width',data=delid)

![image](https://github.com/user-attachments/assets/edbc4997-ae52-4fb5-a39e-d05656511d32)


# Z SQUARE

    import matplotlib.pyplot as plt
    import pandas as pd
    import pandas as pd
    import numpy as np
    import scipy.stats as stats
    dataset=pd.read_csv("/content/heights.csv")
    dataset

![image](https://github.com/user-attachments/assets/0411ee38-2caf-4172-9d8d-ecc05088d5bd)



    df = pd.read_csv("heights.csv")
    q1 = df['height'].quantile(0.25)
    q2 = df['height'].quantile(0.5)
    q3 = df['height'].quantile(0.75)
    iqr = q3-q1
    iqr

![image](https://github.com/user-attachments/assets/8fe723ab-b82b-4642-a3e8-24188456409b)



    low = q1 - 1.5*iqr
    low

![image](https://github.com/user-attachments/assets/1b7f21f9-7d7d-4e78-a235-16a915b2c463)



    high = q3 + 1.5*iqr
    high

![image](https://github.com/user-attachments/assets/2e5ded9c-2b24-4256-a31c-e501c3381482)



    df1 = df[((df['height'] >=low)& (df['height'] <=high))]
    df1

![image](https://github.com/user-attachments/assets/eb1c1029-4b1a-414f-9b7d-8eff5ed363b0)



    z = np.abs(stats.zscore(df['height']))
    z

![image](https://github.com/user-attachments/assets/d1aa234b-4b93-445b-842b-2a38a6f2d37a)



     df1 = df[z<3]
     df1

 ![image](https://github.com/user-attachments/assets/d665ac28-40cb-41da-8990-f04dffb3b778)



# Result

     Thus the Data Cleaning Process and Detecting and Removal of Outliers is executed successfully.
