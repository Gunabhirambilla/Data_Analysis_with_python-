# Data_Analysis_with_python-
IPL DATA SET ANALYSIS WITH PYTHON LIBRARIES

# reading data into python.
df= pd.read_csv(r"C:\Users\gunab\Downloads\cricket data set.csv")
df


# In[3]:


#detailed info of the dataset.
df.info()

# first ten rows of the dataset.
df.head(10)


# last 10 rows of the datset.
df.tail(10)

# basic statistical data of the dataset.
df.describe()


# column names of the dataset.
# deleted unwanted rows from the dataset(Result,umpire3) using del df['column_name'] syntax.
df.columns


# No of rows and columns in the data set.
df.shape


# unique values in the column.
df['city'].unique()

# renaming the columns accordingly.
df.rename(columns = {'id':'Match_id','season':'IPL_Year','player_of_match':'Man_of_the_match'},inplace=True)
df

# column names after renaming them.
df.columns


# replacing null values with other values in the data set
df['umpire1'].fillna(value = 'no umpire',inplace = True)
df['umpire2'].fillna(value = 'no umpire',inplace = True)
df['city'].fillna(value = 'Mumbai',inplace = True)


df.tail(10)

# replacing null values with other values in the data set and printing last 10 rows of dataset.
df['Man_of_the_match'].fillna(value = 'no player',inplace = True)
df['winner'].fillna(value = 'Tie',inplace = True)
df.tail(10)

# finding the null values in each column.
null_counts = df.isnull().sum()
null_counts[null_counts > 0].sort_values(ascending=False)


# max values in each column.
df.max()

# Standard deviation of each column
df.std()


# In[17]:


# mean of each column.
df.mean()

df.median()

df.columns

# co-relation between the columns
#match_id and season are highly co-related.
#Season and winner are highly co-related.
#Match_id and winner are highly co-related.

df.corr()

from sklearn.linear_model import LinearRegression

lr_model = LinearRegression()
lr_model.fit('Match_id','season')


