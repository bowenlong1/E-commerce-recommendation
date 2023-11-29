import pandas as pd
import matplotlib.pyplot as plt
from matplotlib.widgets import SpanSelector

# Your data
data = {
    'days_past_due': list(range(1, 91)),
    'low_defi_high_pay': [37, 71, 120, 74, 93, 99, 91, 69, 56, 68, 56, 51, 61, 79, 163, 107, 16, 114, 90, 6, 125, 102, 3, 79, 73, 7, 108, 111, 6, 74, 60, 5, 65, 51, 5, 73, 61, 6, 31, 28, 5, 42, 38, 4, 120, 38, 1, 112, 100, 1, 82, 103, 18, 99, 91, 20, 114, 96, 21, 89, 91, 15, 74, 82, 17, 74, 64, 29, 19, 11, 17, 46, 54, 39, 50, 76, 85, 50, 37, 47, 37, 58, 48, 76, 21, 25, 12, 9, 33, 10, 9, 13, 17, 12, 18, 3, 2, 18, 2, 19, 11, 4, 9, 2, 15],
    'low_defi_med_pay': [24, 73, 146, 96, 119, 149, 159, 125, 103, 103, 98, 86, 104, 138, 272, 193, 24, 165, 135, 15, 235, 211, 22, 152, 148, 9, 138, 179, 15, 146, 140, 14, 101, 130, 9, 161, 127, 1, 116, 104, 12, 148, 130, 14, 103, 88, 19, 94, 116, 15, 96, 88, 7, 60, 82, 28, 102, 94, 27, 60, 62, 21, 61, 58, 12, 40, 36, 26, 42, 33, 46, 39, 33, 42, 46, 51, 57, 52, 58, 54, 25, 85, 44, 50, 46, 30, 37, 42, 47, 58, 54, 58, 28, 52, 3, 5, 44, 3, 48, 11, 6, 28, 7, 25],
    'low_defi_low_pay': [0, 3, 20, 8, 10, 21, 17, 16, 17, 9, 8, 6, 9, 11, 14, 13, 0, 6, 6, 0, 15, 15, 1, 15, 7, 0, 12, 20, 1, 23, 15, 0, 12, 24, 5, 6, 1, 5, 33, 24, 1, 28, 45, 4, 41, 45, 2, 28, 26, 1, 37, 27, 3, 52, 29, 75, 76, 71, 85, 71, 50, 44, 39, 46, 50, 75, 76, 52, 9, 56, 8, 78, 62, 6, 39, 6, 43],
    'high_defi_high_pay': [43, 71, 120, 74, 93, 99, 91, 69, 56, 68, 56, 51, 61, 79, 163, 107, 16, 114, 90, 6, 125, 102, 3, 79, 73, 7, 108, 111, 6, 74, 60, 5, 65, 51, 5, 73, 61, 6, 31, 28, 5, 42, 38, 4, 120, 38, 1, 112, 100, 1, 82, 103, 18, 99, 91, 20, 114, 96, 21, 89, 91, 15, 74, 82, 17, 74, 64, 29, 19, 11, 17, 46, 54, 39, 50, 76, 85, 50, 37, 47, 37, 58, 48, 76, 21, 25, 12, 9, 33, 10, 9, 13, 17, 12, 18, 3, 2, 18, 2, 19, 11, 4, 9, 2, 15],
    'high_defi_med_pay': [1, 28, 45, 4, 41, 45, 2, 28, 26, 1, 37, 27, 3, 52, 29, 75, 76, 71, 85, 71, 50, 44, 39, 46, 50, 75, 76, 52, 9, 56, 8, 78, 62, 6, 39, 6, 43, 21, 25, 12, 20, 13, 8, 9, 27, 24, 24, 28, 29, 2, 27, 19, 5, 22, 22, 11, 19, 3, 14, 24, 6, 13, 28, 15, 19, 16, 14, 12, 21, 18, 22, 25, 22, 1, 3, 20, 2, 23, 19, 2, 19, 2, 15],
    'high_defi_low_pay': [37, 71, 120, 74, 93, 99, 91, 69, 56, 68, 56, 51, 61, 79, 163, 107, 16, 114, 90, 6, 125, 102, 3, 79, 73, 7, 108, 111, 6, 74, 60, 5, 65, 51, 5, 73, 61, 6, 31, 28, 5, 42, 38, 4, 120, 38, 1, 112, 100, 1, 82, 103, 18, 99, 91, 20, 114, 96, 21, 89, 91, 15, 74, 82, 17, 74, 64, 29, 19, 11, 17, 46, 54, 39, 50, 76, 85, 50, 37, 47, 37, 58, 48, 76, 21, 25, 12, 9, 33, 10, 9, 13, 17, 12, 18, 3, 2, 18, 2, 19, 11, 4, 9, 2, 15],
}

# Function to update the status bar
def update_status(selected_data):
    total_sum = sum(selected_data)
    percentage = total_sum / 34001 * 100
    print(f"Selected Sum: {total_sum}, Percentage: {percentage:.2f}%")

# Create a figure and plot the data
fig, (ax_low, ax_high) = plt.subplots(1, 2, figsize=(15, 6))

# Plot for low defi
ax_low.plot(data['days_past_due'], data['low_defi_high_pay'], label='High Pay')
ax_low.plot(data['days_past_due'], data['low_defi_med_pay'], label='Med Pay')
ax_low.plot(data['days_past_due'], data['low_defi_low_pay'], label='Low Pay')
ax_low.set_xlabel('Days Past Due')
ax_low.set_ylabel('Counts')
ax_low.set_title('Low Defi')
ax_low.legend()

# Plot for high defi
ax_high.plot(data['days_past_due'], data['high_defi_high_pay'], label='High Pay')
ax_high.plot(data['days_past_due'], data['high_defi_med_pay'], label='Med Pay')
ax_high.plot(data['days_past_due'], data['high_defi_low_pay'], label='Low Pay')
ax_high.set_xlabel('Days Past Due')
ax_high.set_ylabel('Counts')
ax_high.set_title('High Defi')
ax_high.legend()

# Create a SpanSelector for low defi
span_low = SpanSelector(ax_low, update_status, 'horizontal', useblit=True, rectprops=dict(alpha=0.5, facecolor='red'))

# Create a SpanSelector for high defi
span_high = SpanSelector(ax_high, update_status, 'horizontal', useblit=True, rectprops=dict(alpha=0.5, facecolor='red'))

plt.show()
