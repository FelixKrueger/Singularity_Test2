Bootstrap: yum
OSVersion: 7
MirrorURL: http://mirror.centos.org/centos-%{OSVERSION}/%{OSVERSION}/os/$basearch/
Include: yum

%help
  This is a test image we're building just to make sure we know how

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
  pip --version
  yum -y groupinstall "Development tools"
  wget https://repo.continuum.io/miniconda/Miniconda2-latest-Linux-x86_64.sh -O ~/miniconda.sh
  bash $HOME/miniconda.sh -b -p $HOME/miniconda
  export PATH="$HOME/miniconda/bin:$PATH"
   # Bioconda (http://ddocent.com//bioconda/)
  conda config --add channels r
  conda config --add channels defaults
  conda config --add channels conda-forge
  conda config --add channels bioconda
  # installing (NextGenMap https://github.com/Cibiv/NextGenMap/wiki)
  conda install -y nextgenmap
  
%runscript
