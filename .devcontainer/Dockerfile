FROM amazonlinux:2

RUN yum -y update && \
    yum install -y sudo shadow-utils procps tar.x86_64 gzip xz unzip witch git && \
    yum install -y python3

RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && \
    unzip awscliv2.zip && \
    ./aws/install && \
    rm -rf ./aws && \
    rm -rf awscliv2.zip

RUN pip3 install git+https://github.com/awslabs/aws-sam-cli

RUN useradd ec2-user
RUN echo "ec2-user ALL=NOPASSWD: ALL" >> /etc/sudoers

USER ec2-user

RUN echo "complete -C '/usr/local/bin/aws_completer' aws" >> ~/.bashrc
