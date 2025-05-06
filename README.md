# Data-Science-task-1



https://colab.research.google.com/drive/1uuZtkxcwZqGQrxIS286KeRH6gdtSzAyb#scrollTo=MS9BtvJ5XyNX




pip install pandas matplotlib

import pandas as pd

# Load the dataset
df = pd.read_csv("/content/API_SP.POP.TOTL_DS2_en_csv_v2_26346.csv", skiprows=4)

# View first few rows
print(df.head())





# Filter for India
india_data = df[df['Country Name'] == 'India']

# Drop unnecessary columns
india_data = india_data.loc[:, '1960':'2022']  # Adjust years based on availability

# Transpose the DataFrame to get years as index
india_data = india_data.T
india_data.columns = ['Population']
india_data.index.name = 'Year'
india_data.reset_index(inplace=True)

print(india_data.head())





import matplotlib.pyplot as plt

# Convert year to int for plotting
india_data['Year'] = india_data['Year'].astype(int)

# Plot the bar chart
plt.figure(figsize=(12, 6))
plt.bar(india_data['Year'], india_data['Population'] / 1_000_000)  # In millions
plt.title('India Population Over Time (in Millions)')
plt.xlabel('Year')
plt.ylabel('Population (Millions)')
plt.grid(True)
plt.tight_layout()
plt.show()





import matplotlib.pyplot as plt

# Example age distribution (synthetic data)
ages = [5, 7, 9, 12, 14, 16, 16, 18, 20, 21, 23, 23, 23, 24, 25, 27, 30, 31, 35, 36, 40, 42, 45, 48, 50, 55, 60, 65, 70]

plt.figure(figsize=(10, 6))
plt.hist(ages, bins=10, color='skyblue', edgecolor='black')
plt.title('Age Distribution of Population')
plt.xlabel('Age')
plt.ylabel('Frequency')
plt.grid(True)
plt.show()






import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load the CSV properly (no skiprows)
df = pd.read_csv("/content/synthetic_population_data.csv")

# Remove any accidental spaces in column names
df.columns = df.columns.str.strip()

# Confirm column names
print(df.columns)

# Plot Age distribution (Histogram)
plt.figure(figsize=(10, 6))
plt.hist(df['Age'], bins=20, color='skyblue', edgecolor='black')
plt.title('Age Distribution of Population')
plt.xlabel('Age')
plt.ylabel('Number of People')
plt.grid(axis='y')
plt.show()

# Plot Gender distribution (Bar Chart)
plt.figure(figsize=(6, 4))
sns.countplot(data=df, x='Gender', palette='Set2')
plt.title('Gender Distribution of Population')
plt.xlabel('Gender')
plt.ylabel('Count')
plt.show()









import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load any CSV file
file_path = "/content/synthetic_population_data.csv"  # 🔁 Change this to your actual file path
df = pd.read_csv(file_path)

# Clean column names
df.columns = df.columns.str.strip()

# Show column names
print("Columns in the dataset:", df.columns.tolist())

# Select the column to visualize
column = "your_column_name"  # 🔁 Replace with column name you want to visualize

# Check if column exists
if column not in df.columns:
    raise ValueError(f"Column '{column}' not found in dataset.")

# Drop missing values
data = df[column].dropna()

# Detect data type
if pd.api.types.is_numeric_dtype(data):
    # Continuous variable → Histogram
    plt.figure(figsize=(10, 6))
    plt.hist(data, bins=20, color='skyblue', edgecolor='black')
    plt.title(f'Distribution of {column}')
    plt.xlabel(column)
    plt.ylabel('Count')
    plt.grid(axis='y')
    plt.show()

else:
    # Categorical variable → Bar Chart
    plt.figure(figsize=(8, 5))
    sns.countplot(x=data, palette='Set2')
    plt.title(f'Distribution of {column}')
    plt.xlabel(column)
    plt.ylabel('Count')
    plt.xticks(rotation=45)
    plt.tight_layout()
    plt.show()






import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns


df = pd.read_csv('/content/synthetic_population_data.csv')

print(df.head())






sns.histplot(df['Age'], bins=10, kde=True, color='skyblue')
plt.title('Age Distribution')
plt.xlabel('Age')
plt.ylabel('Count')
plt.show()




sns.countplot(x='Gender', data=df, palette='Set2')
plt.title('Gender Distribution')
plt.xlabel('Gender')
plt.ylabel('Count')
plt.show()




