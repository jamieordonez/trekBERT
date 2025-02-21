import pandas as pd
import re

# Step 1: Remove rows where Dialogue is missing
df_cleaned = df1.dropna(subset=['Dialogue']).copy()

# Step 2: Fill missing Character names with 'Unknown'
df_cleaned['Character'] = df_cleaned['Character'].fillna('Unknown')

# Step 3: Remove rows that primarily contain metadata in the Dialogue field
# Assuming metadata usually doesn't have speaking characters associated with it
df_cleaned = df_cleaned[df_cleaned['Character'] != 'Unknown']

# Step 4: Define a text-cleaning function
def clean_text(text):
    text = re.sub(r'\[.*?\]', '', text)  # Remove text within brackets
    text = re.sub(r'[^a-zA-Z0-9\s.,!?\'\"]', '', text)  # Remove special characters except basic punctuation
    text = re.sub(r'\s+', ' ', text).strip()  # Remove extra spaces
    return text

# Apply the cleaning function to the Dialogue column
df_cleaned['Dialogue'] = df_cleaned['Dialogue'].astype(str).apply(clean_text)

# Optional: Save the cleaned data to a new CSV file
df_cleaned.to_csv('Cleaned_Star_Trek_Script.csv', index=False)

# Display the first few rows to verify the changes
print(df_cleaned.head())
