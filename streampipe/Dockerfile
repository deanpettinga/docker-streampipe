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
   wget https://github.com/BUStools/bustools/releases/download/v0.39.3/bustools_linux-v0.39.3.tar.gz && \
   tar zxf bustools_linux-v0.39.3.tar.gz && \
   rm bustools_linux-v0.39.3.tar.gz

   # install miniconda3
RUN wget --quiet https://repo.anaconda.com/miniconda/Miniconda3-4.5.11-Linux-x86_64.sh -O ~/miniconda.sh && \
   /bin/bash ~/miniconda.sh -b -p /opt/conda && \
   rm -f ~/miniconda.sh && \
   /opt/conda/bin/conda clean -tipsy && \
   ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
   echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc && \
   echo "conda activate base" >> ~/.bashrc && \
   /opt/conda/bin/conda upgrade -n base conda
   # install snakemake
   /opt/conda/bin/conda install -c bioconda -c conda-forge snakemake==5.9.1

ENV PATH=/opt/conda/bin:/usr/bin/kallisto:/usr/bin/bustools:$PATH
