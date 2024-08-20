# Use Ubuntu 20.04 as the base image
FROM ubuntu:20.04

# Set environment variables
ENV ANSIBLE_VERSION=2.9.17
ENV DEBIAN_FRONTEND=noninteractive

# copy all files from the current directory to the /ansible directory in the container
COPY . /ansible


# Update the package list and install necessary packages
RUN apt-get update && \
    apt-get install -y gcc python3 python3-pip openssh-client openssh-server sshpass && \
    apt-get clean all && \
    rm -rf /var/lib/apt/lists/*

# Upgrade pip and install Ansible
RUN pip3 install --upgrade pip && \
    pip3 install "ansible==${ANSIBLE_VERSION}"

    # allow ssh user named mateo and password secret123
RUN useradd -m -s /bin/bash mateo && \
    echo "mateo:secret123" | chpasswd

# Verify Ansible installation
RUN ansible --version

# Set the working directory
WORKDIR /ansible

# Start the SSH service
RUN service ssh start

# Define default command
CMD ["/usr/sbin/sshd", "-D"]
