FROM ubuntu:15.10

MAINTAINER Adrián Blanco Fernández

RUN apt-get update && \
    apt-get install -y curl && \
    apt-get install -y openssh-server && \
    apt-get install software-properties-common && \
    apt-get -y install git

# Install NODE
RUN curl -sL https://deb.nodesource.com/setup_4.x | bash && apt-get install -y nodejs

# Create new user
RUN useradd -ms /bin/bash userDocker && \
    echo "userDocker:12345" | chpasswd

# Update version NPM
RUN npm install -g npm

# Install Heroku
RUN add-apt-repository "deb https://cli-assets.heroku.com/branches/stable/apt ./" &&  \
    curl -L https://cli-assets.heroku.com/apt/release.key | apt-key add - && \
    apt-get update && \
    apt-get install heroku



EXPOSE 8080

CMD ["/usr/sbin/sshd", "-D"]
