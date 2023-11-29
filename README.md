import pandas as pd
from pandasgui import show
import os

# Your corrected data
data = {
    'days_past_due': list(range(1, 6)),
    'low_defi_high_pay': [37, 71, 120, 74, 93],
    'low_defi_med_pay': [24, 73, 146, 96, 119],
    'low_defi_low_pay': [0, 3, 20, 8, 10],
    'high_defi_high_pay': [43, 73, 120, 74, 93],
    'high_defi_med_pay': [43, 73, 120, 74, 93],
    'high_defi_low_pay': [43, 3, 20, 8, 10],
}

# Create a DataFrame
df = pd.DataFrame(data)

# Specify the icon path directly (you might need to adjust the path)
icon_path = 'path/to/icon.ico'

# Show the DataFrame in an interactive GUI
gui = show(df, icon_path=icon_path)

# Display the GUI
gui.show()
