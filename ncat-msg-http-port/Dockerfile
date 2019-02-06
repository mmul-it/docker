# Raoul Scarazzini (rasca@mmul.it)
# Sample Dockerfile to operate on environment variables, the ports and to
# understand the build process.

# Don't use fedora here, ncat will fail
# See https://github.com/nmap/nmap/issues/1410
FROM ubuntu:latest

# Define environment variables
ENV NCAT_MESSAGE "Container test"
ENV NCAT_HEADER "HTTP/1.1 200 OK"
ENV NCAT_PORT "8888"

# Install nmap packages (contains ncat command)
RUN apt-get update && \
    apt-get install -y nmap && \
    apt-get clean

# Execute ncat so that it will listen and print the message on http
CMD /usr/bin/ncat -l $NCAT_PORT -k -c "echo $NCAT_HEADER; echo; echo $NCAT_MESSAGE"

# Expose the ports (useful mostly for orchestrators)
EXPOSE $NCAT_PORT
