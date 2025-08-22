# Alzhimer's-Project
Histogram Analysis of selected numeric markers (Abeta, pTau, pTDP43, NeuN+, IBA1+, GFAP+) from the Allen Brain Institute MTG neuropathology CSV. Focused on a subset of the data to explore neuronal activity and Alzheimer's-related patterns.

Data focused on within this code is the total at8 positive area grey matter (pTau protiens) and Abeta (amyloid-beta) protiens. *ONLY focused on these numeric columns from the CSV. 

This was a beginner project, so it only shows a histogram as a visual. 

# Start

import pandas as pd
import matplotlib.pyplot as plt

# This is where I loaded my CSV data into code

csv_path =r"C:\Users\djadc\Computation Projects\neu_project\sea-ad_all_mtg_quant_neuropath_bydonorid_081122.csv"
df = pd.read_csv(csv_path)


# Time to clean the imported data up since its not ready
df.columns = [c.strip().replace(" ","_").lower() for c in df.columns]

# Picking my Columns

columns_i_wish_to_analyze = ['total_at8_positive_area_grey_matter','guhcl_abeta42_grey_matter']
for col in columns_i_wish_to_analyze:
    print(f"\nstats for {col}:")
    print("Mean:", df[col].mean())
    print("Median:", df[col].median())
    print("Max:", df[col].max())
    print("Min:", df[col].min())

# Histogram Plotting
for col in columns_i_wish_to_analyze:                                                           
    plt.figure()
    plt.hist(df[col], bins = 20, color='lightblue', edgecolor= 'black')
    plt.title(f"Histogram of [col]")
    plt.xlabel(col)
    plt.ylabel("Frequency")
    plt.show()

  # END
