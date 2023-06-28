# Marge_multiple_CSV_to_one


```python
import os
import pandas as pd

def combine_csv_files(folder_path, output_file):
    # Get all CSV file names in the folder
    file_names = [file for file in os.listdir(folder_path) if file.endswith('.csv')]

    # Initialize an empty DataFrame to store the combined data
    combined_data = pd.DataFrame()

    # Iterate through each file
    for file_name in file_names:
        # Read the CSV file into a DataFrame
        file_path = os.path.join(folder_path, file_name)
        data = pd.read_csv(file_path)

        # Append the data to the combined DataFrame
        combined_data = combined_data.append(data, ignore_index=True)

    # Save the combined data to a new CSV file
    combined_data.to_csv(output_file, index=False)
    print(f"Combined CSV files saved to: {output_file}")

# Example usage
folder_path = '/path/to/csv/folder'
output_file = '/path/to/output/combined.csv'
combine_csv_files(folder_path, output_file)
```

