import pandas as pd

# Loading dataset
df = pd.read_csv("KaggleV2-May-2016.csv")
print("Initial shape:", df.shape)
print(df.head())

# Checking for missing values
print("\nMissing values:\n", df.isnull().sum())

# Removing duplicate rows
print("\nDuplicated before:", df.duplicated().sum())
df = df.drop_duplicates()
print("Duplicated after:", df.duplicated().sum())

# Standardizing column names
df.columns = df.columns.str.strip().str.lower().str.replace(" ", "_")

print("\nColumns after renaming:\n", df.columns)

# Converting date columns to datetime format
df['scheduledday'] = pd.to_datetime(df['scheduledday'])
df['appointmentday'] = pd.to_datetime(df['appointmentday'])

# Filtering out invalid age values
df = df[(df['age'] >= 0) & (df['age'] <= 120)]

# Cleaning 'gender' column (uppercase and strip spaces)
df['gender'] = df['gender'].str.strip().str.upper()

# Renaming 'no-show' to 'no_show' and mapping
df.rename(columns={'no-show': 'no_show'}, inplace=True)
df['no_show'] = df['no_show'].map({'No': 0, 'Yes': 1})

# Saving cleaned dataset to CSV
df.to_csv("Cleaned_medical_appointments.csv", index=False)

print("\nCleaned data shape:", df.shape)
print("Cleaned dataset saved as 'Cleaned_medical_appointments.csv'")
