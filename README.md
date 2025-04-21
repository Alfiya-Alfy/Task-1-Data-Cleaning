# Task-1-Data-Cleaning
import pandas as pd

df = pd.read_csv('appointments.csv')  # change to your actual file name
df.info()
df.describe()
df.head()
# Find missing values
df.isnull().sum()
df.drop_duplicates(inplace=True)
# Standardizing gender, for example
df['Gender'] = df['Gender'].str.upper().str.strip()
# Standardizing country names or responses
df['Country'] = df['Country'].str.title().str.strip()
df['AppointmentDate'] = pd.to_datetime(df['AppointmentDate'], format='%Y-%m-%d')
df.columns = [col.strip().lower().replace(' ', '_') for col in df.columns]
df['age'] = df['age'].astype(int)
df.to_csv('cleaned_appointments.csv', index=False)


