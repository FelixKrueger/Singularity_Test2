Bootstrap: yum
OSVersion: 7
MirrorURL: http://mirror.centos.org/centos-%{OSVERSION}/%{OSVERSION}/os/$basearch/
Include: yum

%help
  This is a test message.

%setup

%labels
    DESCRIPTION Singularity image containing all requirements for a SlamDunk installation
    VERSION 1.0

%post
  yum -y install wget
  yum -y install epel-release
  yum -y update
  yum -y install bzip2
  yum -y install python-pip
  yum -y install tar
  yum -y install which
  
  echo "Installing Development Tools YUM group"
  yum -y groupinstall "Development tools"
  
  wget https://repo.continuum.io/miniconda/Miniconda2-latest-Linux-x86_64.sh -O $HOME/miniconda.sh
  bash $HOME/miniconda.sh -b -p $SINGULARITY_ROOT/opt/miniconda
  export PATH="$SINGULARITY_ROOT/opt/miniconda/bin:$PATH"
 
  # Bioconda (http://ddocent.com//bioconda/)
  conda config --add channels r
  conda config --add channels defaults
  conda config --add channels conda-forge
  conda config --add channels bioconda
  conda create -y --name SlamDunk -c bioconda slamdunk
 
  # Installing Bowtie2
  conda install bowtie2=2.3.0
  
  %environment
  #Set your toolname here and the appropriate version to have this in the metadata of your container
    #BOWTIE2=v2.3.0
  
%runscript
