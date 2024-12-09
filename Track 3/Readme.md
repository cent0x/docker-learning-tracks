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
import redis
from fastapi import FastAPI

app = FastAPI()

# Connect to Redis
redis_client = redis.Redis(host='redis', port=6379, db=0)

@app.get("/")
def read_root():
    redis_client.incr('hits')
    hits = redis_client.get('hits').decode('utf-8')
    return {"message": "Hello World", "hits": hits}

@app.get("/items/{item_id}")
def read_item(item_id: int, q: str = None):
    redis_client.set(f'item:{item_id}', q)
    stored_value = redis_client.get(f'item:{item_id}').decode('utf-8')
    return {"item_id": item_id, "stored_value": stored_value}
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
redis
```

7. **Create the `Dockerfile`**:
   - In the root of your project directory, create a `Dockerfile`:
Dockerfile

   - Add the following content to the `Dockerfile`:
```Dockerfile
#Get the latest image Pythton:3.14-slim
FROM python:3.13-slim

WORKDIR /code

#Copy requirements file
COPY ./requirements.txt ./

RUN pip install --no-cache-dir -r requirements.txt

COPY ./src ./src

CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "80", "--reload"]
```


## Automate Docker creation using YML

Create `docker-compose.yml` file in parent directory 

```yml
services:
  app:
    build: .
    container_name: python-cont
    command: uvicorn src.main:app --host 0.0.0.0 --port 80 --reload
    ports:
      - 80:80
    volumes:
      - .:/code

  redis:
    image: "redis:latest"
    container_name: redis-cont
    ports:
    - "6379:6379"
```

Run `docker compose`

```sh
 docker compose up --build -d
 ```


### Access the Application

Open your web browser and go to `http://localhost:80`. Any changes you make to `main.py` in the `src` directory will be automatically reflected in the running container.