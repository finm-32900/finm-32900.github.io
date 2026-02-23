


ssh [username]@midway3.rcc.uchicago.edu
squeue -u [username]
sinfo
accounts balance

Project directory in 
/project/finm32900/

module avail
module load python/anaconda-2024.10


module load scode python/anaconda-2024.10




Helpful info:

---
RCC (University of Chicago Research Computing Center) home directories typically have a 25 GB to 30 GB quota, designed for storing source code, configuration files, and installed software, rather than large datasets. These directories are backed up hourly (to disk) and daily (to tape), unlike scratch space. 
GitHub
GitHub
 +1
Key Storage Details:
Home Directory (/home/$USER): ~25-30 GB quota.
Project Space (/project2/$GROUP): Large allocations available, typically 1 TB+ depending on PI, intended for long-term storage.
Scratch Space (/scratch/midway2/$USER): 100 GB to 5 TB, intended for active job processing, not backed up. 
GitHub
GitHub
 +1
Users can check their usage by running the quota command on the login nodes. If more space is required in the home directory, users may need to move files to /project/ or /scratch/ or request, via their PI, a quota increase. 
The University of Chicago
The University of Chicago
 +1
 ---



Tutorial:
Show how to use:

scode serve-web -- --account <pi-account> --time 01:00:00 --mem 16G
scode serve-web -- --account finm32900 --time 01:00:00 --mem 16G

I get this:
```
[jbejarano@midway3-login4 case_study_clean_trace]$ scode serve-web -- --account finm32900 --time 01:00:00 --mem 16G
Removing existing symlink: /home/jbejarano/.vscode/cli/serve-web/072586267e68ece9a47aa43f8c108e0dcbf44622.
Linked /home/jbejarano/.scode/versions/stable/1.109.5/vscode-server-linux-x64-web to /home/jbejarano/.vscode/cli/serve-web/072586267e68ece9a47aa43f8c108e0dcbf44622
Submitting SBATCH to serve VSCode environment.

Submitted batch job 45863567

sbatch: Verify job submission ...
sbatch: Using a shared partition ...
sbatch: Partition: caslake
sbatch: QOS-Flag: caslake
sbatch: Account: finm32900
sbatch: Verification: ***PASSED***

SBATCH job /home/jbejarano/.scode/sbatches/scode-web_20260223_105124.sbatch submitted successfully.
Output will be directed to /home/jbejarano/.scode/logs/scode-web_45863567.out.
Errors will be directed to /home/jbejarano/.scode/logs/scode-web_45863567.err.

VSCode server is starting with Slurm Job ID 45863567.
Use `scode jobs status 45863567` to get server status and connection info.
Use `scancel 45863567` to cancel the server job.

VSCode job 45863567 is running on 1 nodes: midway3-0067
Primary node: 10.50.250.67
Environment: /home/jbejarano/.scode/envs/stable/default

To connect to the VSCode Web GUI you need to create an SSH tunnel from your local machine to the primary node above. This can be done with the following command to be run on your local machine (e.g., PowerShell in Windows):

    ssh -L 8000:10.50.250.67:58992 jbejarano@midway3.rcc.uchicago.edu

Once the tunnel is created, you may access the VSCode Web GUI by entering the following address in your browser:

    http://localhost:8000/?tkn=SOME_LONG_TOKEN

Server outputs are being written to /home/jbejarano/.scode/logs/scode-web_45863567.out.
Server errors are being written to /home/jbejarano/.scode/logs/scode-web_45863567.err.
Use `squeue -j 45863567` to check the status of the job.
Use `scancel 45863567` to cancel the job.
```

---

Note that it is my preference above to add the -N flag when port forwarding.

Add -N (no command) and optionally -f (background) so SSH only does port forwarding and never opens a shell.