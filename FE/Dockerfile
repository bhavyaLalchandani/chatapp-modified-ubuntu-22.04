FROM ubuntu:22.04

# Install Nginx
RUN apt-get update && apt-get install -y nginx && apt-get clean

# Copy the Nginx configuration file
COPY FE/chatapp.conf /etc/nginx/sites-available/chatapp.conf

# Create a symbolic link in sites-enabled
RUN ln -s /etc/nginx/sites-available/chatapp.conf /etc/nginx/sites-enabled/

# Remove the default Nginx configuration
RUN rm -rf /etc/nginx/sites-enabled/default

# Expose port 80 for Nginx
EXPOSE 80

# Start Nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]
