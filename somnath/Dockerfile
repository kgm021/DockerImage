# Use the official Nginx image as the base image
FROM nginx:latest

# Copy a custom configuration file to replace the default Nginx configuration
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Create a directory for your custom HTML file
RUN mkdir -p /usr/share/nginx/html/tajmahal

# Copy the HTML file with "Taj Mahal" content to the custom directory
COPY tajmahal.html /usr/share/nginx/html/index.html

# Expose port 80 for web traffic
EXPOSE 80

# Start Nginx when the container starts
CMD ["nginx", "-g", "daemon off;"]
