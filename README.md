import pandas as pd
import matplotlib.pyplot as plt
from matplotlib.widgets import SpanSelector

# Your corrected data
data = {
    'days_past_due': list(range(1, 91)),
    'low_defi_high_pay': [37, 71, 120, 74, 93, 99, 91, 69, 56, 68, 56, 51, 61, 79, 163, 107, 16, 114, 90, 6, 125, 102, 3, 79, 73, 7, 108, 111, 6, 74, 60, 5, 65, 51, 5, 73, 61, 6, 31, 28, 5, 42, 38, 4, 120, 38, 1, 112, 100, 1, 82, 103, 18, 99, 91, 20, 114, 96, 21, 89, 91, 15, 74, 82, 17, 74, 64, 29, 19, 11, 17, 46, 54, 39, 50, 76, 85, 50, 37, 47, 37, 58, 48, 76, 21, 25, 12, 9, 33, 10, 9, 13, 17, 12, 18, 3, 2, 18, 2, 19, 11, 4, 9, 2, 15],
    'low_defi_med_pay': [24, 73, 146, 96, 119, 149, 159, 125, 103, 103, 98, 86, 104, 138, 272, 193, 24, 165, 135, 15, 235, 211, 22, 152, 148, 9, 138, 179, 15, 146, 140, 14, 101, 130, 9, 161, 127, 1, 116, 104, 12, 148, 130, 14, 103, 88, 19, 94, 116, 15, 96, 88, 7, 60, 82, 28, 102, 94, 27, 60, 62, 21, 61, 58, 12, 40, 36, 26, 42, 33, 46, 39, 33, 42, 46, 51, 57, 52, 58, 54, 25, 85, 44, 50, 46, 30, 37, 42, 47, 58, 54, 58, 28, 52, 3, 5, 44, 3, 48, 11, 6, 28, 7, 25],
    'low_defi_low_pay': [0, 3, 20, 8, 10, 21, 17, 16, 17, 9, 8, 6, 9, 11, 14, 13, 0, 6, 6, 0, 15, 15, 1, 15, 7, 0, 12, 20, 1, 23, 15, 0, 12, 24, 5, 6, 1, 5, 33, 24, 1, 28, 45, 4, 41, 45, 2, 28, 26, 1, 37, 27, 3, 52, 29, 75, 76, 71, 85, 71, 50, 44, 39, 46, 50, 75, 76, 52, 9, 56, 8, 78, 62, 6, 39, 6, 43],
    'high_defi_high_pay': [43, 71, 120, 74, 93, 99, 91, 69, 56, 68, 56, 51, 61, 79, 163, 107, 16, 114, 90, 6, 125, 102, 3, 79, 73, 7, 108, 111, 6, 74, 60, 5, 65, 51, 5, 73, 61, 6, 31, 28, 5, 42, 38, 4, 120, 38, 1, 112, 100, 1, 82, 103, 18, 99, 91],
    'high_defi_med_pay': [43, 73, 120, 74, 93, 99, 91, 69, 56, 68, 56, 51, 61, 79, 163, 107, 16, 114, 90, 6, 125, 102, 3, 79, 73, 7, 108, 111, 6, 74, 60, 5, 65, 51, 5, 73, 61, 6, 31, 28, 5, 42, 38, 4, 120, 38, 1, 112, 100, 1, 82, 103, 18, 99, 91, 20, 114, 96, 21, 89, 91, 15, 74, 82, 17, 74, 64, 29, 19, 11, 17, 46, 54, 39, 50, 76, 85, 50, 37, 47, 37, 58, 48, 76, 21, 25, 12, 9, 33, 10, 9, 13, 17, 12, 18, 3, 2, 18, 2, 19, 11, 4, 9, 2, 15],
    'high_defi_low_pay': [43, 3, 20, 8, 10, 21, 17, 16, 17, 9, 8, 6, 9, 11, 14, 13, 3, 6, 6, 0, 15, 15, 1, 15, 7, 0, 12, 20, 1, 23, 15, 0, 12, 24, 5, 6, 1, 5, 33, 24, 1, 28, 45, 4, 41, 45, 2, 28, 26, 1, 37, 27, 3, 52, 29, 75, 76, 71, 85, 71, 50, 44, 39, 46, 50, 75, 76, 52, 9, 56, 8, 78, 62, 6, 39, 6, 43],
}

# Create a DataFrame
df = pd.DataFrame(data)

# Function to update the plot based on the selected range
def update_plot(min_val, max_val):
    selected_data = df[(df['days_past_due'] >= min_val) & (df['days_past_due'] <= max_val)]
    total_value = selected_data.iloc[:, 1:].sum().sum()
    percentages = selected_data.iloc[:, 1:].sum() / total_value * 100
    ax2.clear()
    percentages.plot(kind='bar', ax=ax2)
    ax2.set_ylabel('Percentage')
    ax2.set_title('Percentage of Selected Data')

# Create the figure and subplots
fig, (ax1, ax2) = plt.subplots(2, 1, figsize=(10, 8), gridspec_kw={'height_ratios': [3, 1]})

# Plot the data
df.plot(x='days_past_due', y=['low_defi_high_pay', 'low_defi_med_pay', 'low_defi_low_pay'], kind='bar', stacked=True, ax=ax1, title='Low Defi')
df.plot(x='days_past_due', y=['high_defi_high_pay', 'high_defi_med_pay', 'high_defi_low_pay'], kind='bar', stacked=True, ax=ax2, title='High Defi')

# Create a SpanSelector for interactive selection
span = SpanSelector(ax1, update_plot, 'horizontal', useblit=True, rectprops=dict(alpha=0.5, facecolor='red'))

plt.show()
