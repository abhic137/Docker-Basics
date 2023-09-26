# Use the official Tomcat image as the base image
FROM tomcat:9.0

# Copy your "Hello, World!" HTML page to Tomcat's webapps directory
COPY index.html /usr/local/tomcat/webapps/ROOT/

# Optionally, you can expose the default Tomcat HTTP port (8080)
EXPOSE 8080

# Start Tomcat when the container is launched
CMD ["catalina.sh", "run"]
