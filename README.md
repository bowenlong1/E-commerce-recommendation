import pandas as pd
from datetime import datetime

# Sample dataframe
data = {'date': ['2023/09/07 17:14:25', '2023/09/08 18:15:26']}
df = pd.DataFrame(data)

def transform_date(date_str):
    # Parse the input date string
    dt = datetime.strptime(date_str, '%Y/%m/%d %H:%M:%S')
    
    # Reformat the date with uppercase for the month part
    new_format = 'DIGITAL ETL: Email sent successfully on ' + dt.strftime('%d%b%y:%H:%M:%S').upper()
    
    return new_format

# Apply the transformation function to the 'date' column
df['date'] = df['date'].apply(transform_date)

print(df)
