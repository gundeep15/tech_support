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

**Step 1**: Type or copy the following commands (separately followed by pressing return) to activate python on the cluster node.

module swap intel gcc

\<return>

module load cuda/10.1

\<return>

module load python/3.7.0

\<return>

*Note: The default shortkey for paste in linux is a right click on the mouse.*

![jupyterstep1.png](https://github.com/gundeep15/tech_support/blob/master/jupyterstep1.png)

**Step 2**: specify the host for running the jupyter notebook on your browser using the following command:

jupyter notebook --no-browser --ip=$(hostname -i) --port=9999

Returning this command would result something as screenshot-ed below indicating the ip address and the corresponding token (password) where the jupyter notebook will be hosted:

![jupyterstep2.png](https://github.com/gundeep15/tech_support/blob/master/jupyterstep2.png)

**Step 3**: Copy or note down the ip-address. 

*Note: DO NOT USE Ctrl+C for copy. It would kill everything. The default command for copy/cut in linux is Ctrl+C*

**Step 4**: **Start a new terminal window**. You can do that by either clicking on the (+) on the windows tab. or using the main tab 'Terminal -> Open new tab'. In the new tab, paste/type the following command with the copied id address:

ssh -N -L 9999:<IP ADDRESS>:9999 <caseID>@rider.case.edu

![jupyterstep3.png](https://github.com/gundeep15/tech_support/blob/master/jupyterstep3.png)

**Step 5**: Open the ip-host on your preferred browser window using http://localhost:9999/tree

**Step 6**: Copy the token and enter as requested on the browser window. *reminder: Ctrl+x for copy. NOT Ctrl+C.*

The token code is specified after http://<IP ADDRESS>:9999/?token=<TOKEN to be copied and pasted into the browser window>

**Step 7**: *almost there* Once you see the Jupyter directories, you have successfully accessed the jupyter connected via the cluster node. 

Open a jupyter notebook, and in the notebook run the following, which should return "True":

import tensorflow as tf

tf.test.is_gpu_available() 

**Step 8**: Finally, you would have to install packages as needed. But since this is hosted by the cluster, you do not have the permission to install packages to the whole server, but you can install them only for your user id. Check the packages already available for you using *!pip list*. For installing new packages, using commands like:

**!pip install --user opencv-python**, where opencv-python is the package name.

You are now set to use the cluster gpu on jupyter!!!

## Mac:  

### CWRU HPC Cluster Access

**Step 1**: Download and install a client-server tool for remote access to the cluster. Recommended is [X2Go](https://wiki.x2go.org/doku.php) appropriate for your system. DMG link for [macOS 10.13 and higher](https://code.x2go.org/releases/X2GoClient_latest_macosx_10_13.dmg) 

**Step 2**: Launch X2Go Client. Start a new session using the main tab 'Session -> New Session...'

![macstep2.png](https://github.com/gundeep15/tech_support/blob/master/macstep2.png)

**Step 3**: Enter the host name as rider.case.edu, specify the Login with your case ID, and keep the port to 22. 

![macstep3.png](https://github.com/gundeep15/tech_support/blob/master/macstep3.png | width=50)


<img src="https://github.com/gundeep15/tech_support/blob/master/macstep3.png" alt="macstep3.png" height="500">
