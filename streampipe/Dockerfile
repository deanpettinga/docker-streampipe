FROM centos:7

   # install tools for CentOS
RUN yum update -y && \
    yum install -y which \
                   wget \
                   bzip2 \
                   git \
                   make \
                   cmake && \

RUN cd /usr/bin/ && \
   # install kallisto
   wget https://github.com/pachterlab/kallisto/releases/download/v0.46.1/kallisto_linux-v0.46.1.tar.gz && \
   tar zxf kallisto_linux-v0.46.1.tar.gz && \
   rm kallisto_linux-v0.46.1.tar.gz && \
   # install bustools
   git clone https://github.com/BUStools/bustools.git && \
   cd bustools && \
   mkdir build && \
   cd build && \
   make && \
   make install

   # install miniconda3
RUN wget --quiet https://repo.anaconda.com/miniconda/Miniconda3-4.5.11-Linux-x86_64.sh -O ~/miniconda.sh && \
   /bin/bash ~/miniconda.sh -b -p /opt/conda && \
   rm -f ~/miniconda.sh && \
   /opt/conda/bin/conda clean -tipsy && \
   ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
   echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc && \
   echo "conda activate base" >> ~/.bashrc && \
   conda upgrade -n base conda
   # install snakemake
   conda install -c bioconda -c conda-forge snakemake==5.9.1

ENV PATH=/opt/conda/bin:/usr/bin/kallisto:/usr/bin/bustools:$PATH
