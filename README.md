Requirements: 

1. Connected to Case Wireless Network, 

2. Added to cluster by the group leader (in this case, Mike) who has already purchased cluster access for their group

## Windows:

### CWRU HPC Cluster Access
**Step 1**: Download and install a client-server tool for remote access to the cluster. Recommended is home version of [Mobaxterm](https://mobaxterm.mobatek.net/download.html).

**Step 2**: Launch Mobaxterm. Start a new SSH session using the tab 'Sessions -> New Session -> SSH'

![windowsstep2.png](https://github.com/gundeep15/tech_support/blob/master/windowsstep2.png)

**Step 3**: Enter the host name as rider.case.edu, specify the username with your case ID, and keep the port to 22. 

![windowsstep3.png](https://github.com/gundeep15/tech_support/blob/master/windowsstep3.png)

Note: At this point you should be connected to Case Wireless to proceed further. In the terminal window on Mobaxterm, you should see the beginning of the command line as connected to the hpc (high performance computing) with a format like '[\<caseID>@hpc3 ~]$'

**Step 4**: Request a gpu (or cpu) cluster node using the following command (or a version of it depending upon your requirements): 

**srun --x11 -p gpu -C gpup100 --gres=gpu:1 -N 1 -c 2 --time=4:00:00 --mem=20gb --pty /bin/bash**

With the above command, you will get the Tesla P100 gpu for a period of 4 hours with memory of 20gb.

For a summary of resources available on the cluster, visit https://sites.google.com/a/case.edu/hpcc/servers-and-storage/cluster-resources

Once you press return, your request is proceeded and you will see the command line change from '[\<caseID>@hpc3 ~]$' to '[\<caseID>@gpu\<node number> ~]$'

![windowsstep4.png](https://github.com/gundeep15/tech_support/blob/master/windowsstep4.png)

Voila! You have now obtained the GPU node.

### Accessing Jupyter on cluster

**Step 1**: Type or copy the following commands (separately) to activate python on the cluster node.

module swap intel gcc

\<return>

module load cuda/10.1

\<return>

module load python/3.7.0

\<return>

*Note: The default shortkey for paste in linux is the right click on mouse.*

![jupyterstep1.png](https://github.com/gundeep15/tech_support/blob/master/jupyterstep1.png)

## Mac:  
Step 1: Download and install a client-server tool for remote access to the cluster. Recommended is [X2Go](https://wiki.x2go.org/doku.php) appropriate for your system. DMG link for [macOS 10.13 and higher](https://code.x2go.org/releases/X2GoClient_latest_macosx_10_13.dmg) 

