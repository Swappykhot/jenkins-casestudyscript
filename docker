# Use Ubuntu as the base image
FROM ubuntu:latest

# Update the package repository and install Apache
RUN apt-get update && \
    apt-get install -y apache2 && \
    apt-get clean

# Copy the website files to the default Apache directory
COPY . /var/www/html/

# Expose port 80
EXPOSE 80

# Start Apache in the foreground
CMD ["apache2ctl", "-D", "FOREGROUND"]
