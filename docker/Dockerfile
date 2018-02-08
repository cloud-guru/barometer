FROM centos:7
RUN yum update -y
RUN yum install -y which sudo
RUN yum install -y git
#RUN yum install -y qpid-proton-c-devel-0.18.1-1.el7.x86_64 --enablerepo=epel-testing
ENV DOCKER y
ENV repos_dir /src

RUN git config --global http.sslVerify false
WORKDIR ${repos_dir}
RUN git clone -b bays_branch https://github.com/aneeshkp/barometer.git
WORKDIR ${repos_dir}/barometer/systems
RUN sh ./build_base_machine.sh
RUN useradd -ms /bin/bash collectd_exec
RUN echo "collectd_exec ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

COPY run_collectd.sh /run_collectd.sh
RUN chmod +x /run_collectd.sh
