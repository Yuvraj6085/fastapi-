# fastapi-

from fastapi import FastAPI, Body

app = FastAPI()

@app.get("/")
def read():
    return {"message": "Hello, World!"}

@app.get("/vi")
def read_version():
    return {"version": "1.0.0"}

@app.post("/vi")
def vie(payload: dict = Body(...)):
    print("Payload received in terminal:")
    print(payload)  # This prints to terminal
    return {"new":f"title { payload['title']} content { payload['content']}"}

from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()

# Define the request model with all your fields
class Post(BaseModel):
    title: str
    content: str
    category: str
    author: str
    created_at: str
    updated_at: str
    published: bool = True

@app.get("/")
def read():
    return {"message": "Hello, World!"}

@app.get("/vi")
def read_version():
    return {"version": "1.0.0"}

@app.post("/vi")
def vie(nwe_post: Post):
    # Print all received data in terminal
    print("Received POST data:")
    print(f"Title: {nwe_post.title}")
    print(f"Content: {nwe_post.content}")
    print(f"Category: {nwe_post.category}")
    print(f"Author: {nwe_post.author}")
    print(f"Created At: {nwe_post.created_at}")
    print(f"Updated At: {nwe_post.updated_at}")
    print(f"Published: {nwe_post.published}")

    # Send confirmation in response
    return {
        "message": "New post received!",
        "data": nwe_post.dict()
    }
