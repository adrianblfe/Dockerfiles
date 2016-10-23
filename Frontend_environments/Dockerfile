FROM ubuntu:15.10

MAINTAINER Adrián Blanco Fernández

RUN apt-get update && \
    apt-get install -y curl && \
    apt-get install -y openssh-server && \
    apt-get -y install git && \
    apt-get -y install sudo
RUN mkdir /var/run/sshd
RUN echo "root:123" | chpasswd
RUN sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

# Install NODE
RUN curl -sL https://deb.nodesource.com/setup_4.x | bash && apt-get install -y nodejs

# Create new user
RUN useradd -ms /bin/bash userDocker && \
    echo "userDocker:12345" | chpasswd

# Update version NPM
RUN npm install -g npm

# Install tools
RUN npm install -g bower
RUN npm install -g grunt-cli
RUN apt-get install -y ruby2.1-dev rubygems build-essential
RUN gem update --system
RUN gem install compass
RUN gem install sass
RUN npm install -g karma karma-cli jasmine
RUN npm install -g phantomjs-prebuilt
RUN npm install -g yo generator-fountain-webapp generator-karma generator-angular

RUN apt-get install -y libfontconfig

# Change permissions npm
# RUN chown -R userDocker $(npm config get prefix)/{lib/node_modules,bin,share}

EXPOSE 9000

CMD ["/usr/sbin/sshd", "-D"]
