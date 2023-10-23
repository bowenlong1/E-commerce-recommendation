from datetime import datetime

def transform_date(date_str):
    # Parse the input date string
    dt = datetime.strptime(date_str, '%Y/%m/%d %H:%M:%S')
    
    # Reformat the date
    new_format = dt.strftime('DIGITAL ETL: Email sent successfully on %d%b%y:%H:%M:%S').upper()
    
    return new_format

date_str = '2023/09/07 17:14:25'
result = transform_date(date_str)
print(result)

