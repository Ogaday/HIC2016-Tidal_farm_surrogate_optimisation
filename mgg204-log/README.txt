Date: Wed 30 Sep 2015
Author: Ogaday Willers Moore (wow202 / wow203)

This text to be found on Mulualem's Computer, hardware identifier: 3033.

At this time I am a researcher working in the Centre for Water Systems at Exeter Uni. The project I am working on is to develop effective meta models for the more expensive CFD simulations of hydro electric generator arrays. The advantage of these cheaper meta or surrogate models is that they can be used in an optimisation algorithm so that the layout of the tidal farm can account for the wake and blockage effect interactions between the turbines in a tidal farm. The turbine in question was developed by Aquascientific and is called the momentum reversal lift turbine (patent: xxxx). However, in order to train these models, it is necessary to have data in the first place. Generating any significant amount of data from a CFD model takes a significant amount of time (months). Fortunately, there is a corpus of information that can be used from previous research. The CFD model itself was developed by another researcher by the name of Mulualem G. Gebraslassie, and this is the computer he used. He left it to us as he is now leaving to return home to Ethopia, so that we ca continue to run CFD simulations, generate data and check our results. The more machine power we have, the better. This was cleared with Professor Michael Belmont, who was Mulualem's suerpvisor.

A few notes, then, now there has been the barest minimum of orientation about our goals and intentions. The application primarily used on this computer will be OpenFOAM (~/OpenFOAM). ~/OpenFOAM/mgg204-2.1.1 is the working directory for Mulualem's OpenFOAM-2.1.1 installation, I believe. Within that, there are three subdirectories of interest: applications, run and swak4foam. swak4foam is some sort of package I think, applications should have a subdirectory "solvers" containing the solvers, in this case TInterfoam (turbine Interfoam, a standard form of solver for OpenFOAM) and run would normally contain the information about the "cases". I believe that in your own installs of OpenFoam these are automatically created. Inside run, Mulualem further subdivides his "cases" between different fields. We are interested in run/postdoc/michele/, which is where he ran the "cases" that we are currrently using as data to train our surrogate models. In that directory, he further divided the cases by "staggered" and "tandem" configuration. We are only interested in "staggered". In there, Mulualem created an example directory for me in order to run some new cases I generated. I will try to document formally the model itself in another document soon. In there, however, are ten cases, set up in directories called ogadayi for i in range(10). However, he also copied that directory elsewhere so that I would be ready to run more of my own simulations. They are located here: /home/mgg204/OpenFOAM/mgg204-2.1.1/run/ogaday and in my own directory here: /home/mgg204/OpenFOAM/mgg204-2.1.1/wow202-2.1.1, which contains it's own run, applications, sqak4foam directories. They are not all synced however, and most up to date one is here: ~/OpenFOAM/mgg204-2.1.1/run/ogaday/staggered/. I will subsequently continue to run the samples there, though I might change the location on the next generation. Currently, ogaday1 is at timestep 5725, ogaday2 at 200, ogaday3 at 1355 and ogaday4 at 1465. These are the most recent timesteps written to disk, every five timesteps are written to disks, and the process terminates at timestep 7000.

When installing swak4foam and TInterfoam on other computers, three .so (shared object, a dynamically shared library) that are present on mulualem's machine are not installed on the other machine. They are libmyPowerTurbulence.so, libmyBCs.so and libfieldFunctionObjectsCustom.so. The first caused FOAM WARNINGS to be thrown when running blockMesh, topoSet, etc... and eventually when running the solver, TInterfoam, it failed and exited immediately. They are thus copied here in this directory, because when copied to $FOAM_USER_LIBBIN on a similau (unix) system, it appears to work.

Directory diagram here:

.
  |-mgg204-2.1.1
  |  |-applications
  |  |  |-solvers
  |  |  |  |-TInterFoam
  |  |-swak4foam
  |  |-run
  |  |  |-postdoc
  |  |  |  |-michele
  |  |  |  |  |-staggered
  |  |  |  |  |  |-Ogaday1
  |  |  |  |  |-applications
  |  |  |  |  |  |-solvers
  |  |  |  |  |  |  |-TInterFoam
  |  |  |  |  |-swak4foam
  |  |  |-ogaday
  |  |  |  |-staggered
  |  |-wow202-2.1.1
  |  |  |-applications
  |  |  |  |-solvers
  |  |  |  |  |-TInterFoam
  |  |  |-swak4foam
  |  |  |-run
  |  |  |  |-staggered
  
The three locations are demonstrated.

There is a small amount of documentation, or at least text files containing the relevant bash commands to use. They are in "command" in the .../run/postdoc/Michele directory and in the pbs files in each generation directory (ie. s-stepi or ogaday5 etc.).

This computer (hardware identifier: 3033)
This file is stored in a snippet on bitbucket: bitbucket.org/snippets/Ogaday/yR9kM/mgg204-log.git
University of Exeter
