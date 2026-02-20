**<h2>Official Documentation</h2>**

###
```python
http://127.0.0.1:8000/docs
```

###
```python
https://127.0.0.1:8000/
```

---

**<h2>Starting</h2>**

###

To start using **API**, you just need the `Python 3.8+` and install with `pip`:

###
```python
pip install api
```

###

> If you want to test the `API` locally, we recommend using the `fast ASGI server`:

###
```python
pip install uvicorn
```

###

> Let's create a simple **API** that responds **"API With FastAPI"**.

###
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def home():
    return {"message": "API With FastAPI"}
```

###

> To run, save the above code in `main.py`:

###
```powershell
uvicorn main:app --reload
```

###

`--reload` restarts the server automatically when there are code changes, great for **development**.

---

Open the navigation and access:

###
```Powershell
http://127.0.0.1:8000/
```

###

**<h2>Parameters</h2>**

###

> You can define parameters in the URL:

###
```python
@app.get("/items/{item_id}")
def read_item(item_id: int):
    return {"item_id": item_id}
```

---

**<h2>Request Body</h2>**

###
```python
from pydantic import BaseModel

class Item(BaseModel):
name: str
price: float

@app.post("/items/")
def create_item(item: Item):
    return item
```

###

> If the sent `JSON` doesn't match the model, the `API` responds with a `422` error and a clear message.

---

**<h2>Automatic Documentation<h2>**

###

> Your **API** will already have **interactive** documentation accessible via:

###
```Powershell
Swagger UI: http://127.0.0.1:8000/docs
```

###
```Powershell
ReDoc: http://127.0.0.1:8000/redoc
```

---

You can test **all** endpoints directly through the browser.

###

- Advanced Settings;
- Middlewares.

###

> You can add **middleware** to intercept requests and responses:

###
```python
@app.middleware("http")
async def log_request(request, call_next):
    print(f"Request for {request.url.path}")

    response = await call_next(request)
    return response
```

###

**<h2>Parameters</h2>**

###

> You can set parameters in the `URL`:

###
```python
@app.get("/items/{item_id}")
def read_item(item_id: int):
    return {"item_id": item_id}
```

###

> Here, `item_id` is a **int** parameter extracted from `URL`.

---

**<h2>Request body</h2>**

###

> To receive data via `JSON`, define  **parameters** with types and **API** automatically validates:

###
```python
from pydantic import BaseModel

class Item(BaseModel):
    nome: str
    preco: float

@app.post("/items/")
def create_item(item: Item):
    return item
```

###

**<h2>Examples of Use</h2>**

###

> Automatic validation with `Pydantic`. **API** integrates the `Pydantic` for validating input and output data.

###
```python
from pydantic import BaseModel

class User(BaseModel):
    name: str
    email: str

@app.post("/usuarios/")
def create_user(user: User):
    return {"mensagem": f"User {user.name} created!"}
```

###

> If `JSON` sent does not match the model, the **API** responds with error `422` and a clear message.

---

**<h2>Automatic Documentation<h2>**

###

> Your **API** will already have documentation **interativa** accessible via: 

###
```powershell
Swagger UI: http://127.0.0.1:8000/docs
```

###
```powershell
ReDoc: http://127.0.0.1:8000/redoc
```

---

> You can test **all** the `endpoints` directly through the **browser**.

###

- Advanced settings;
- `Middlewares`.

###

**<h2>Security and Authentication</h2>**

###

- API offers integrated support for `OAuth2`, `JWT`, `API Keys` and other strategies;
- Always define models for input and output data;
- Use automatic validation to avoid common mistakes;
- Document each route with comments for easy maintenance;
- Use documentation tools to test your `API` often;
- Keep your server updated to take advantage of security improvements.

---

**<h2>Extras</h2>**

###

> `env` is in `.gitignore`, you need to create it every time you use it.

###
```
grater than = gt ### greater than...
grater or equal = ge ### greater than or equal to...
lower than = lt ### less than...
lower or equal = le ### less than or equal to...
```
