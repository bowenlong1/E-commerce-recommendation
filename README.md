import pandas as pd
from datetime import datetime

# Sample dataframe
data = {'date': ['2023/09/07 17:14:25', '2023/09/08 18:15:26']}
df = pd.DataFrame(data)

def transform_date(date_str):
    # Parse the input date string
    dt = datetime.strptime(date_str, '%Y/%m/%d %H:%M:%S')
    
    # Reformat the date
    new_format = dt.strftime('DIGITAL ETL: Email sent successfully on %d%b%y:%H:%M:%S').upper()
    
    return new_format

# Apply the transformation function to the 'date' column
df['date'] = df['date'].apply(transform_date)

print(df)
