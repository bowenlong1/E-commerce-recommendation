Hi Fiza,

Following our meeting,

Please refer to the "eot_pipeline_0416.sas" file for the EOT SAS data pipeline. This has also been shared with MLOPs, and Erwin is currently validating the new fields added. Once the validation for the new fields is complete, they will proceed with code conversion for us.

Here are a few key points to focus on for the EOT strategy:

1) Update the prediction threshold (1/3 for each group) and deficiency balance threshold (2/3 low deficiency balance) based on the latest workable portfolio from January to April 2024. The data can be found here, excluding weekends, holidays, and holds such as promise/curtesy, etc.:

```sas
libname ic '/opt/SAS/SAS_data/projects/DATASCIENCE/RPT/dev/Custom_Data/AAA_Data Science Projects/Collections/Data/Servicing IB Calls';
ic.eot_wkb_janapr2024
```

2) Based on the newly determined thresholds and the latest workable portfolio, update the holdout strategy to achieve a 20% workload reduction. For January to April 2024 data, the designed workable holdout for non-tax only accounts is 50%, and for tax-only accounts is 70%, to meet the 20% workload reduction target. Refer to the highlighted tabs of the attached Excel file ("v2 workable design - checkbox.xlsm") for details on the non-tax only strategy and workable holdout estimation. Additionally, I have attached SAS code ("holdout_estimation.sas") to calculate daily workable and workload accounts.

For all files related to the EOT project, please access the following directory:

```
\\americredit.com\db_files\Data_Science\Data_Science\Servicing Projects\Lease EOT Strategy
```

Please let me know if you have any questions or need further clarification.

Best regards,

[Your Name]
