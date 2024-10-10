Getting started with Argon
==========================

Accessing Argon
---------------
detail: `(wiki) Argon Access <https://uiowa.atlassian.net/wiki/spaces/hpcdocs/pages/76513416/Accessing+HPC+resources>`_

* On campus or off campus with VPN

  .. code-block:: bash
   
     ssh HawkID@argon.hpc.uiowa.edu
  ..

* Off campus without VPN

  .. code-block:: bash

     ssh -p 40 HawkID@argon.hpc.uiowa.edu
  ..

.. note::

   The activation of VPN is recommended for security when you access outside campus.

----

Evironment modules on Argon
---------------------------
detail: `(wiki) Argon Environment Modules <https://uiowa.atlassian.net/wiki/spaces/hpcdocs/pages/76513436/Environment+Modules>`_

.. option:: module list

   list currently loaded modules

   .. code-block:: bash

      dooyoon@argon-itf-login-4 ~> module list

      Currently Loaded Modules:
        1) stack/2021.1
   ..

.. option:: module avail [package]

   search information of the package under the current stack

.. option:: module spider [package]

   search detailed information of the package in all stacks

.. option:: module load [package]

   load the module 

.. option:: module unload [package]

   unload the module

.. option:: module reset

   set the environment to the default configuration

.. option:: module purge

   remove all modules 
   

----

SGE Jobs
--------
details: `(wiki) basic job submission <https://uiowa.atlassian.net/wiki/spaces/hpcdocs/pages/76513450/Basic+Job+Submission>`_ and `(wiki) advanced job submission <https://uiowa.atlassian.net/wiki/spaces/hpcdocs/pages/76513452/Advanced+Job+Submission>`_

.. option:: qsub [job script]

   submit a job with batch script

.. option:: qstat -u [HawkID]

   check the state of the submitted job

   :status: * r:   running
            * qw:  waiting in the queue

.. option:: qdel [job ID number]

   cancel the submitted job either waiting in the queue or running

.. option:: qlogin [option]

   interactive SGE session for a requested time period

   :option -  SGE derivatives: * -q [queue name]
                               * -pe smp [number of slots]    
                               * ...

----

**Sample batch script for a job submission**

.. code-block:: bash
   :name: sample_job_script

   #!/bin/bash

   #####Set Scheduler Configuration Directives#####
   # Set the name of the job.
   # This will be the first part of the job's .o (output) and .e (error) file names.
   #$ -N sleeper

   # By default, the job's working directory is the $HOME directory.
   # Here, set it the same as the current working directory when the job was submitted.
   # The job's .o (output) and .e (error) files will be written here.
   #$ -cwd

   # Send e-mail at beginning/end/suspension of job:
   #$ -m bes

   # E-mail address to send to:
   #$ -M [your Iowa email address]
   #####End Set Scheduler Configuration Directives#####

   #####Resource Selection Directives#####
   # Provide a comma-separated list of queues the scheduler can consider for this job:
   #$ -q [queue name]

   # Specify the number of slots the job will use:
   #$ -pe smp [number of slots]
   #####End Resource Selection Directives#####

   #####Load Modules####
   #module reset
   #module load ...
   #####Load Modules####

   #####Begin Compute Work#####
   # During the job, print information to stdout, which will be written into the job's output file:
   /bin/echo "Running on compute node: $(hostname)."
   /bin/echo "In directory: $(pwd)"
   /bin/echo "Starting on: $(date)"

   # Invoke the programs we want to run, and provide any necessary input parameters.
   # First, we start the "sleep" command so that it waits 60 seconds, then exits:
   sleep 60

   # Print the end date of the job before exiting:
   echo "Job ended: $(date)"
   #####End Compute Work#####
..
