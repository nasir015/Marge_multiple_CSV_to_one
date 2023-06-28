# Marge_multiple_CSV_to_one

import glob
import pandas as pd
import os

def combine_multiple_csv_to_one_csv(folder_path,output_folder_path):
    file_names = [file for file in os.listdir(folder_path) if file.endswith('.csv')]
    k = []
    for file_names in file_names:
        file_path = os.path.join(folder_path, file_names)
        k.append(file_path)

    l = []
    for file in k:
        df = pd.read_csv(file, index_col=None, header=0)
        l.append(df)

    for i in range(len(l)):
        pd.DataFrame(l[i]).to_csv(output_folder_path, mode='a', header=False)

folder_path = 'E:\\Programming_Practice\\final_dataset'
output_folder_path = 'E:Programming_Practice\\final_dataset\\final_dataset.csv'
combine_multiple_csv_to_one_csv(folder_path,output_folder_path)
