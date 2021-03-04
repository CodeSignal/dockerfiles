FROM codesignal/ubuntu-base:new

# Install Nim
RUN curl https://nim-lang.org/choosenim/init.sh -sSf | sh -s -- -y

# Set path to Nim compiler
ENV PATH /root/.nimble/bin:$PATH
