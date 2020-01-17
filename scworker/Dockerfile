FROM centos:7

    # install tools for CentOS
RUN yum update -y && \
    yum install -y which \
                   python3 \
                   epel-release \
                   git \
                   wget \
                   bzip2 \
                   cmake && \
    yum install -y R
    # overwrite python3 as default python

    # install R packages
RUN R -e 'install.packages("Matrix", repos="http://cran.us.r-project.org")' && \
    R -e 'install.packages("BiocManager", repos="http://cran.us.r-project.org")' && \
    R -e 'BiocManager::install("DropletUtils", repos="http://cran.us.r-project.org")' && \
    R -e 'BiocManager::install("SingleR", repos="http://cran.us.r-project.org")'

    # install python deps
RUN pip3 install --force-reinstall \
      scanpy==1.4.3 \
      scvelo==0.1.24 \
      h5py==2.9.0 \
      numpy==1.17.4 \
      pandas==0.25.3 \
      plotly==4.3.0 \
      scikit-learn==0.21.3 \
      scipy==1.3.2 \
      umap-learn==0.3.10 \
      python-igraph==0.7.1.post6 \
      Matplotlib==3.0.3

    # install scworker
#RUN git clone https://github.com/trichelab/scworker.git /usr/bin/scworker
