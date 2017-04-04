# build with : sudo docker build -t singularity .
FROM debian:stretch
RUN apt -y update && apt -y dist-upgrade && apt install -y ffmpeg mediainfo git wget unp sox build-essential autoconf automake unp vim-nox bc
RUN mkdir /source
RUN cd /source && pwd && git clone https://github.com/brontosaurusrex/singularity
RUN wget https://downloads.sourceforge.net/project/opencore-amr/fdk-aac/fdk-aac-0.1.5.tar.gz -O /source/fdk.tar.gz
RUN cd /source && unp fdk.tar.gz && cd fdk-aac-0.1.5 && ./configure && make && make install
RUN cd /source && git clone https://github.com/nu774/fdkaac && cd fdkaac && pwd && autoreconf -i && ./configure && make && make install
RUN cd /source/singularity/bin && cp * /usr/local/bin 
RUN sed -i.bak s/\$HOME//g /usr/local/bin/singularity.cfg
RUN cd /usr/local/bin && sed -i 's/\$HOME\/bin\//\/usr\/local\/bin\//g' * 
RUN mkdir -p /output/log
#CMD ["singularitySomeChecks"]
