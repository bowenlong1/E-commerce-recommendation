Hi Fiza,

Per our meeting,

please see “eot pipeline 0416.sas” for the EOT sas data pipeline, which has been also shared with MLOPs, and Erwin is doing validation for the new fields added, after new fields validation pass, they will start code conversion for us.

Here are few things you might have to focus for EOT strategy.

1)	Update the prediction threshold (1/3 each group) and deficiency balance threshold (2/3 low deficiency balance) based on latest workable portfolio Jan-Apr 2024

The data is saved here, excluding weekends, holidays and promise/curtesy etc holds
libname ic '/opt/SAS/SAS_data/projects/DATASCIENCE/RPT/dev/Custom_Data/AAA_Data Science Projects/Collections/Data/Servicing IB Calls';

ic.eot_wkb_janapr2024
2)	Based on new theresholds determined and latest workable portfolio, refresh the holdout strategy to meet the 20% workload reduction.Based on janapr 2024 data, the design workable holdout for non-tax only accounts is 50%, for tax-only accounts is 70% in order to meet the 20% workload reduction target.
See highlighted tabs of attached excel (v2 workable design - checkbox.xlsm) for the non-tax only strategy details and workable holdout estimation, Also I attached sas code to calculate daily workable and workload accounts “holdout estimation.sas”

For all files of EOT project, please refer to \\americredit.com\db_files\Data_Science\Data_Science\Servicing Projects\Lease EOT Strategy

