This directory contains Auryn classes and simulations to reproduce on-line
learning with orchestrated plasticity rules. 

This is the development branch to run with Auryn > v0.7.  
Tested with Auryn develop branch commit
7d834eb6d2be03a411031d4e12a876f44227109f


# Auryn classes

P10Connection 
       Implements the excitatory connection object for orchestrated
       plasticity without homeostatic sliding threshold.

P11Connection 
       Implements the excitatory connection object for orchestrated
       plasticity with homeostatic sliding threshold.

P12Connection 
       Implements variation of P11Connection with two limits of the
       sliding threshold.


# Running an example

This simulation reproduces the key results from the orchestrated plasticity
simulation as described in Figure 3 you need to install and compile Auryn
(commit 7d834eb6) Note, that due to ongoing development of the simulator and
specifically changes to the random seeding of SparseConnections since v0.4.1
the network you are simulating is not identical at the individual connection
level to the simulation shown in the paper. To replicate the original
simulation bit-by-bit please refer to the commit history of this repository and
the simulator.

In the following we will assume that you have git installed and up and running
on your system. Moreover, you have all dependencies to compile Auryn installed.

To download and compile Auryn do the following:
$ cd ~
$ git clone https://github.com/fzenke/auryn.git
$ cd auryn/build/home
$ make

Should you have difficulties compiling the simulator please refer to the
installation and troubleshooting section in the manual (www.fzenke.net/auryn).

Now go to the installation directory of the simulation code (when you are
reading this, chances are you are already in this directory) and run make there
(you might have to update the auryn path in the Makefile if you are using a
different install directory). This will build the necessary Auryn libraries
that implement plasticity and the simulation libraries. The binary file
sim_rc_p10c is the downstream file of the simulation behind Figure 3 in Zenke,
F., Agnes, E.J., Gerstner, W., 2015. Diverse synaptic plasticity mechanisms
orchestrated to form and retrieve memories in spiking neural networks. Nature
Communications.

Finally, update the output path in 'globalvars.sh' to point to a portion of
disk with sufficient space. If you want to run distributed simulations make
sure this path is accessible from all nodes of your cluster.

Invoking
$ ./run_orchestrated_stdp.sh
will run the three scripts 1run_init.sh, 2run_learn.sh and 3run_cued.sh and
the necessary bootstrap script in sequence which corresponds to the two-fold
learning and recall protocol shown in Figure 3.