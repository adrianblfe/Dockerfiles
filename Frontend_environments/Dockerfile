FROM ubuntu:15.10

MAINTAINER Adrián Blanco Fernández

EXPOSE 8080

RUN apt-get update && \
    apt-get install -y curl && \
    apt-get install -y openssh-server && \
    apt-get -y install git && \
    apt-get -y install sudo && \
    mkdir /var/run/sshd && \
    echo "root:123" | chpasswd && \
    sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd && \
    curl -sL https://deb.nodesource.com/setup_6.x | bash && apt-get install -y nodejs && \
    useradd -ms /bin/bash userDocker && \
    echo "userDocker:12345" | chpasswd && \
    npm install -g npm && \
    npm install -g lite-server && \
    npm install -g babel-cli && \
    npm install -g babel-preset-es2015 && \
    npm install -g webpack && \
    apt-get install -y ruby2.1-dev rubygems build-essential && \
    gem update --system && \
    gem install compass && \
    gem install sass && \
    npm install -g karma karma-cli jasmine && \
    npm install -g phantomjs-prebuilt && \
    apt-get install -y libfontconfig


CMD ["/usr/sbin/sshd", "-D"]


# SSH login fix. Otherwise user is kicked off after login

# Install NODE

# Create new user

# Update version NPM

# Install tools


# RUN chown -R userDocker $(npm config get prefix)/{lib/node_modules,bin,share}
# Change permissions npm
