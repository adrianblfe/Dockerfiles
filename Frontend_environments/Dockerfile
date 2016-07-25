FROM ubuntu:15.10

MAINTAINER Adrián Blanco Fernández

EXPOSE 9000:9000

RUN apt-get update && apt-get install -y curl && apt-get install -y openssh-server && apt-get -y install git
RUN mkdir /var/run/sshd
RUN echo "root:123" | chpasswd
RUN sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

# Install NODE
RUN curl -sL https://deb.nodesource.com/setup_4.x | bash && apt-get install -y nodejs

# Create new user
RUN useradd -ms /bin/bash userDocker

# Update version NPM
RUN npm install -g npm

# Install tools
RUN npm install -g bower
RUN npm install -g grunt-cli
RUN npm install -g coffee-script
RUN apt-get install -y ruby-full rubygems
RUN gem install sass
RUN npm install -g karma karma-cli jasmine
RUN npm install -g phantomjs-prebuilt
RUN npm install -g yo generator-fountain-webapp generator-karma generator-angular

RUN npm update -g minimatch@3.0.2

RUN apt-get install -y libfontconfig

# Change to new user
USER userDocker
WORKDIR /home/userDocker

CMD ["/usr/sbin/sshd", "-D"]
