## IGWN-install-MacOS

[General instructions](https://computing.docs.ligo.org/conda/)

Step-by-step instructions:

1. [Install Fuse for MacOS](https://osxfuse.github.io/)
2. [Install CVMFS file system](https://ecsft.cern.ch/dist/cvmfs/cvmfs-2.3.5/cvmfs-2.3.5.pkg)
3. [Configure CVFMS](https://www.gw-openscience.org/cvmfs/)
   1. **cd /etc/cvmfs/**
   2. create and edit default.local to have this one line:  
   *CVMFS_HTTP_PROXY=DIRECT*
   3. **cd /etc/cvmfs/default.d/**
   4. create and edit 60-osg.conf to have these lines:  
 *\# /etc/cvmfs/default.d/60-osg.conf. 
 \#  
 \# DO NOT EDIT THIS FILE  
 \# It will be replaced on upgrade. To override, edit /etc/cvmfs/default.local  
 \#  
 CVMFS_SEND_INFO_HEADER=yes  
 CVMFS_KEYS_DIR=/etc/cvmfs/keys/opensciencegrid.org  
 CVMFS_USE_GEOAPI=yes  
 CVMFS_CONFIG_REPOSITORY=config-osg.opensciencegrid.org   
 CVMFS_CONFIG_REPO_REQUIRED=yes  
 CVMFS_FALLBACK_PROXY=http://cvmfsbproxy.cern.ch:3126;http://cvmfsbproxy.fnal.gov:3126  
 create and edit config-osg.opensciencegrid.org.conf to have single line:  
 CVMFS_SERVER_URL=http://cvmfs-s1bnl.opensciencegrid.org:8000/cvmfs/@fqrn@;http://cvmfs-s1fnal.opensciencegrid.org:8000/cvmfs/@fqrn@;http://cvmfs-s1goc.opensciencegrid.org:8000/cvmfs/@fqrn@*  
   5. create these directories:  
   **sudo mkdir -p /cvmfs/config-osg.opensciencegrid.org**  
   **sudo mkdir -p /cvmfs/oasis.opensciencegrid.org**  
   **sudo mkdir /cvmfs/gwosc.osgstorage.org**
   6. mount these directories to cvmfs:  
   **sudo mount -t cvmfs config-osg.opensciencegrid.org /cvmfs/config-osg.opensciencegrid.org**  
   **sudo mount -t cvmfs oasis.opensciencegrid.org /cvmfs/oasis.opensciencegrid.org**  
   **sudo mount -t cvmfs gwosc.osgstorage.org /cvmfs/gwosc.osgstorage.org**   
4. To find the bulk data from observation runs, change to    
   **cd /cvmfs/gwosc.osgstorage.org/**
5. In new terminal window you should now be able to navigate   
   **ls -lh /cvmfs/oasis.opensciencegrid.org**
6. For example  
   **ls -lh /cvmfs/oasis.opensciencegrid.org/ligo/sw**  
   should list the following software:  
   **conda  lalsuite  lscsoft  pycbc**  
7. [Install Miniconda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html) (both python2.7 and python3.7)
8. Check that miniconda python is in the path with   
   **echo $PATH**
9. To see which python installation is the default:  
   **which python**
10. Check which packages are in your current conda environment:  
   **conda list**
11. Add the conda-forge channel:  
   **conda config --add channels conda-forge**
12. Download the [igwn-py27](https://computing.docs.ligo.org/conda/environments/igwn-py27/) and [igwn-py37](https://computing.docs.ligo.org/conda/environments/igwn-py37/) YAML files (OSX versions).
13. Install the environments locally  
   **conda env create --file igwn-py27.yaml**  
   **conda env create --file igwn-py37.yaml**  
14. List the installed invironments   
   **conda env list**
15. Activate an environment  
   **conda activate igwn-py27**
16. Deactivate an environment  
   **conda deactivate**
   


   
   
   
