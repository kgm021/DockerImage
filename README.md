# DockerImage
- docker image prepare and push to ACR.
    
    To configure an Nginx Docker image to display "Taj Mahal" when accessed with the path "/tajmahal" and then push the image to an Azure Container Registry (ACR) from your local laptop, you can follow these steps:
    
    **Step 1: Create an HTML File**
    
    First, create an HTML file that will display "Taj Mahal" when accessed. Create a file named `index.html` with the following content:
    
    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <title>Taj Mahal</title>
    </head>
    <body>
        <h1>Taj Mahal</h1>
        <p>This is the Taj Mahal.</p>
    </body>
    </html>
    
    ```
    
    **Step 2: Create a Dockerfile**
    
    Next, create a Dockerfile to build a custom Nginx image that serves the `index.html` file when accessed with the "/tajmahal" path. Create a file named `Dockerfile` with the following content:
    
    ```
    # Use the official Nginx image as the base image
    FROM nginx
    
    # Copy the custom HTML file to the Nginx HTML directory
    COPY index.html /usr/share/nginx/html
    
    # Create a custom Nginx configuration to handle the "/tajmahal" path
    RUN echo "location /tajmahal { root /usr/share/nginx/html; index index.html; }" > /etc/nginx/conf.d/custom.conf
    
    ```
    
    **Step 3: Build the Docker Image**
    
    Open a terminal, navigate to the directory where the `Dockerfile` and `index.html` files are located, and build the Docker image:
    
    ```bash
    docker build -t my-nginx-tajmahal .
    
    ```
    
    **Step 4: Test the Docker Container Locally**
    
    Run the Docker container locally to test if it displays "Taj Mahal" when accessed with the "/tajmahal" path:
    
    ```bash
    docker run -d -p 80:80 my-nginx-tajmahal
    
    ```
    
    You can access the content by opening a web browser and navigating to http://localhost/tajmahal.
    
    **Step 5: Push the Docker Image to Azure Container Registry**
    
    Before pushing the Docker image to your Azure Container Registry (ACR), make sure you have already logged in to your Azure account using the Azure CLI. If not, run:
    
    ```bash
    az login --tenant 18791e17-6159-4f52-a8d4-de814ca8284a
    ```
    
    Then, log in to your ACR:
    
    ```bash
    az acr login --name kavyagmacr
    ```
    
    Finally, push the Docker image to your ACR:
    
    ```bash
    docker tag tajmahal kavyagmacr.azurecr.io/tajmahal:latest
    docker push kavyagmacr.azurecr.io/tajmahal:latest
    
    ```
    
    Now, the Docker image with the custom Nginx configuration is pushed to your Azure Container Registry and can be used for deployments in Azure or any other Docker-compatible environment.
