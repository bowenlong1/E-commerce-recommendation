proc power;
     twosamplefreq
          test		= pchi	/* Pearson’s chi-squared test */
          alpha		= 0.05	/* Type 1 error, typically 5% */
          power 		= 0.8	/* Power, typically 80% */
          groupweights 	= (50 50)	/* Control vs Treatment */
          ntotal 		= .	/* Sample size needed.  This is what we are to determine */
          refproportion	= 0.0711	/* Control group proportion */
          proportiondiff 	= 0.001 0.002 0.003 0.004 0.005 0.007 0.01 0.015 0.02 0.025 0.03/* Estimated impact of the intervention.  p2-p1 */
          sides		= 1	/* Sides of the test.  Typically 1 sided if the direction of impact is known */
;
run;
