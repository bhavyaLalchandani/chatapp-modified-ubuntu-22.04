FROM ubuntu:22.04

# Update the package list and install required dependencies
RUN apt-get update && \
    apt-get install -y python3 python3-pip python3-dev default-libmysqlclient-dev build-essential git && \
    apt-get clean

# Create the directory for your app
# RUN mkdir /myChatapp

# Copy your Django app into the container
# COPY my-chatapp /myChatapp

RUN git clone https://github.com/bhavyaLalchandani/chatapp-modified-ubuntu-22.04 /myChatapp

# Set the working directory for your app in the container
WORKDIR /myChatapp

# Install required Python packages from requirements.txt
RUN pip3 install -r requirements.txt

RUN apt install python3-dev default-libmysqlclient-dev build-essential pkg-config -y
RUN apt-get update
# Install the MySQL client library for Python
RUN pip3 install mysqlclient

# Expose port 8000 for Django
EXPOSE 8000

# Set the working directory to the Django app's folder and run migrations
WORKDIR /myChatapp/fundoo/

# Start the Django server after running migrations
ENTRYPOINT python3 manage.py migrate && python3 manage.py runserver 0.0.0.0:8000
