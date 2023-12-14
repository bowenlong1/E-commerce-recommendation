import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd

def plot_daily_change(df, variable, day1, day2):
    df['dt'] = pd.to_datetime(df['day_key'], format='%Y%m%d')
    day = df[(day1 <= df.day_key) & (df.day_key <= day2)]

    unique_categories = df[variable].unique()

    for category in unique_categories:
        df[f'{variable}_{category}_cat'] = 0
        df.loc[df[variable] == category, f'{variable}_{category}_cat'] = 1

        category_df = pd.DataFrame(df.groupby('dt')[f'{variable}_{category}_cat'].agg(['size', 'sum']).reset_index())
        category_df['ratio'] = category_df['sum'] / category_df['size']

        sns.lineplot(data=category_df, x="dt", y="ratio", label=f'{variable}: {category}')

    plt.xticks(rotation=45)
    plt.title(f'Daily Ratio Change for {variable}')
    plt.xlabel('Date')
    plt.ylabel('Ratio')

    # Adjust legend size and orientation
    plt.legend(title=f'{variable} Categories', bbox_to_anchor=(1.05, 1), loc='upper left')

    plt.show()

# Set your day1 and day2 variables here
day1 = 20231023
day2 = 20231212

# Set your dataframe df here
# Example: df = ...

# List of categorical variables
categorical_variables = ['cat_dpd_6_mnth_max', 'cat_dpd_5_mnth_max', 'cat_dpd_2_mnth_max']

# Generate line plots for each categorical variable with all categories
for variable in categorical_variables:
    plot_daily_change(df, variable, day1, day2)

