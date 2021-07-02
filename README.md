# Functional MRI Data Preprocessing
To pre-process fmri data, I apply atlas containing gordon and harvard-oxford

# Preparing Data
- untar.sh : Untar each frmiprep tar data
- duplicate_untar.sh : Duplicate untared frmi data just in case

# Before using Job Scheduler
- timeseries.py : Apply atlas to extract timeseries data
- atlas_one.sh :  Apply timeseries.py code to a fmriprep of one subject
- atlas.sh : Apply timeseries.py code to all of the fmri data

# After using Job Scheduler
- time_create_jobs.py : create jobs.txt
- jobs.txt : create commands for all subjects' fmri data
(ex) /scratch/bigdata/ABCD/abcd-fmriprep-rs/time.sh /scratch/bigdata/ABCD/abcd-fmriprep-rs/abcd-fmriprep-rs-untar/fmriprep-deri-NDARINV0CTJAAHC/fmriprep/sub-NDARINV0CTJAAHC/ses-baselineYear1Arm1/func/sub-NDARINV0CTJAAHC_ses-baselineYear1Arm1_task-rest_run-1_space-MNIPediatricAsym_cohort-4_res-2_desc-preproc_bold.nii.gz /scratch/bigdata/ABCD/abcd-fmriprep-rs/abcd-fmriprep-rs-time/fmriprep-deri-NDARINV0CTJAAHC

# Final using Job Scheduler
- make_each_job.sh : Dividing commands of jobs.txt into each subjects and saving as sh files

# Common Use
- time.sh : Apply timeseries.py code to a fmriprep of one subject (similar to atlas_one.sh)

# Details
each subject has several fmriprep images in terms of run
some subjects have 1~4 runs, others have 3 runs and the others have 5~6 runs
-> all names of the job text files include run number

# Basic command
- qstat -f: check the queues
- qconf -sc: check the options of job
- qstat: check the running job
- qdel: stop the running queue

# Qsub options
- -q all.q: using all of the queues
- -l h_vmem: set the maximum memory amount
- -cwd: job file which I want to run
- -N: set the job name
