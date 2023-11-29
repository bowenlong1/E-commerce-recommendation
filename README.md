import pandas as pd
import matplotlib.pyplot as plt
from matplotlib.widgets import SpanSelector

# Your data
data = {
    'days_past_due': list(range(1, 91)),
    'high_pay_1': [59, 142, 371, 280, 345, 333, 283, 236, 173, 161, 150, 152, 171, 177, 423, 242, 23, 222, 182, 12, 286, 253, 19, 174, 149, 25, 167, 178, 13, 122, 103, 7, 104, 94, 5, 102, 61, 6, 45, 34, 3, 47, 39, 6, 26, 19, 0, 26, 29, 2, 28, 19, 1, 18, 23, 1, 28, 19, 0, 16, 26, 16, 23, 30, 21, 14, 12, 21, 18, 17, 25, 22, 25, 22, 1, 3, 20, 2, 23, 19, 2, 19, 2, 15],
    'med_pay_1': [16, 62, 155, 84, 116, 151, 139, 118, 95, 68, 52, 62, 74, 83, 168, 115, 15, 108, 87, 6, 145, 139, 15, 93, 81, 11, 97, 118, 8, 95, 73, 6, 67, 88, 3, 108, 98, 6, 83, 66, 7, 113, 113, 4, 91, 77, 3, 86, 110, 9, 85, 73, 8, 60, 61, 29, 74, 61, 40, 58, 44, 58, 44, 4, 5, 49, 0, 61, 46, 3, 60, 4, 64],
    'low_pay_1': [0, 3, 20, 8, 10, 21, 17, 16, 17, 9, 8, 6, 9, 11, 14, 13, 0, 6, 6, 0, 15, 15, 1, 15, 7, 0, 12, 20, 1, 23, 15, 0, 12, 24, 5, 6, 1, 5, 33, 24, 1, 28, 45, 4, 41, 45, 2, 28, 26, 1, 37, 27, 3, 52, 29, 75, 76, 71, 85, 71, 50, 44, 39, 46, 50, 75, 76, 52, 9, 56, 8, 78, 62, 6, 39, 6, 43]
}

df = pd.DataFrame(data)

# Function to update the status bar
def update_status(selected_data):
    total_sum = sum(selected_data)
    percentage = total_sum / 34001 * 100
    print(f"Selected Sum: {total_sum}, Percentage: {percentage:.2f}%")

# Create a figure and plot the data
fig, ax = plt.subplots(figsize=(10, 6))
ax.plot(df['days_past_due'], df['high_pay_1'], label='High Pay')
ax.plot(df['days_past_due'], df['med_pay_1'], label='Med Pay')
ax.plot(df['days_past_due'], df['low_pay_1'], label='Low Pay')
ax.set_xlabel('Days Past Due')
ax.set_ylabel('Counts')
ax.legend()

# Create a SpanSelector to handle the selection
span = SpanSelector(ax, update_status, 'horizontal', useblit=True, rectprops=dict(alpha=0.5, facecolor='red'))

plt.show()
