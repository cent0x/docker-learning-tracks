# Track 1: Setting Up a Simple Web Server
___


Description: Create a Docker container that runs a basic web server using Nginx.

Technologies: Docker, Nginx

Learning Outcomes: Understand how to create and run containers, expose ports, and serve static content.
## Procedure
___
1. **Create the HTML file**:
   - First, create a directory for your project and navigate into it.
   - Create a subfolder webpage 

2. Get static webpages from the Internet
    - Visit https://html5up.net/ to choose for site templates

3. **Create a Dockerfile**:
   - In the same directory, create a `Dockerfile` to set up the web server.

   ```dockerfile
   # Use an official nginx image as the base image
   FROM nginx:alpine

   # Copy the HTML file to the nginx html directory
   COPY static /usr/share/nginx/html/

   # Expose port 80
   EXPOSE 80

   # Start nginx
   CMD ["nginx", "-g", "daemon off;"]
   ```

4. **Build the Docker image**:
   - Open a terminal, navigate to your project directory, and build the Docker image.

   ```sh
   docker build -t nginx-img .
   ```

5. **Run the Docker container**:
   - Run the container using the image you just built.

   ```sh
   docker run -d -p 80:80 nginx-img
   ```

This will start a simple static web server with your contact information and address. You can access it by navigating to `http://localhost` in your web browser.


6. **Run the Docker container**:
   - Delete or Modify this
   
```Dockerfile
# Copy the HTML file to the nginx html directory
  COPY static /usr/share/nginx/html/
```
   - Run the container using the image you just built.

```sh
docker run -d -p 80:80 -v "$(pwd)/static:/usr/share/nginx/html" nginx-img
```
