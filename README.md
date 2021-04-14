# python-fastapi-tutorial

I tried python fastapi.
The reason is not to develop a REST API service using python. 

The purpose is to create a mock quickly and create a REST API specification quickly.

I feel that fastapi is better than JSON Server. Also, I use fastapi when writing REST APIs in Python.

Dockerfile
```
FROM tiangolo/uvicorn-gunicorn-fastapi:python3.7

COPY ./app /app
```

main.py
```
from typing import Optional
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"Hello": "World"}

@app.get("/items/{item_id}")
def read_item(item_id: int, q: Optional[str] = None):
    return {"item_id": item_id, "q": q}
```

Directory
```
├── app
│   └── main.py
└── Dockerfile
```

Build Docker Image
```
docker build -t myimage .
```

Run Docker Container
```
docker run -d --name mycontainer -p 8000:80 myimage
```

Confirm using Browser

http://localhost:8000/items/5?q=somequery
http://localhost:8000/docs
http://localhost:8000/redoc

