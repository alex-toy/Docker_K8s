FROM ubuntu:latest

# Install ping utilities
RUN apt-get update && apt-get install -y iputils-ping

# Optional: Set a command to keep the container running
CMD ["tail", "-f", "/dev/null"]

