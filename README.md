/* Example SAS code to calculate sample size for t-test */
proc power;
  twosamplemeans
    test=t
    meansdiff =  /* estimated impact of the intervention. mean2 - mean1 */
    groupweights = (weight1 weight2) /* Specify the proportions or weights for each group */
    stddev = /* Standard deviation of the continuous variable */
    ntotal = . /* specify the total sample size, or set to missing to calculate */
    npergroup = .; /* specify the number of subjects in each group, or set to missing to calculate */
  ods select TTests;
run;
