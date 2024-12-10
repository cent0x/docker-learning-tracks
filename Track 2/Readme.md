
### Step-by-Step Guide

1. **Open Terminal**:
   - Launch PowerShell if not default

2. **Create a New Project Directory**:
 - Navigate to the location where you want to create your project directory.
   - Create a new directory for your project:
```sh
mkdir fastapi-docker
cd fastapi-docker
code .
```
- This will open a new VScode window
- Open the terminal in VSCode (Ctrl + `).

3. **Create the `src` Directory**:
   - Inside your project directory, create a `src` directory:
```sh
mkdir src
```

4. **Create `main.py` Inside `src`**:
   - Navigate into the `src` directory and create the `main.py` file:

5. **Add Code to `main.py`**:
   - Open `main.py` in VSCode and add the following code:
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Hello, World!"}

# To run the server, use the command: uvicorn filename:app --reload

```

6. **Create `requirements.txt`**:
   - Go back to the root of your project directory and create a `requirements.txt` file:
```sh
cd ..
touch requirements.txt
```
   - Add the following dependencies to `requirements.txt`:
```
fastapi
uvicorn
```

7. **Create the `Dockerfile`**:
   - In the root of your project directory, create a `Dockerfile`:
Dockerfile

   - Add the following content to the `Dockerfile`:
```Dockerfile
# Use the official Python image from the Docker Hub
FROM python:3.13-slim

# Set the working directory in the container
WORKDIR /code

# Copy the requirements file into the container
COPY ./requirements.txt ./

# Install the dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the application code into the /src directory
COPY ./src ./src

# Command to run the application with auto-reload
CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8000", "--reload"]
```

8. **Build and Run the Docker Container**:
   - Build the Docker image:
```sh
docker build -t fastapi .
```

9. **Analyzing the use of Volume**

- Run the Docker container without the volume mounting

```powershell
docker run -d -p 8000:8000 fastapi
```

   - Run the Docker container with volume mounting:


```powershell
docker run -d -p 8000:8000 -v ${PWD}:/code fastapi
```


### Access the Application

Open your web browser and go to `http://localhost:8000`. Any changes you make to `main.py` in the `src` directory will be automatically reflected in the running container.

## Automate Docker creation using YML

Create `docker-compose.yml` file in parent directory 

```yml
services:
  app:
    build: .
    container_name: python-cont
    command: uvicorn src.main:app --host 0.0.0.0 --port 8000 --reload
    ports:
      - "8000:8000"
    volumes:
      - .:/code
```

Run `docker compose`

```sh
 docker compose up --build -d
 ```
