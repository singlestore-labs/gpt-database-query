# Database Query GPT

**Attention**: The code in this repository is intended for experimental use only and is not fully tested, documented, or supported by SingleStore. Visit the [SingleStore Forums](https://www.singlestore.com/forum/) to ask questions about this repository.

## Run Development Environment

1. Create a Python environment by running:

```sh
python3 -m venv .venv
```

2. Active the environment by running:

```sh
source .venv/bin/activate
```

3. Install dependencies by running:

```sh
pip install -r requirements.txt
```

4. Run the app.py run running:

```sh
nodemon app.py
```

## Create a HTTP Tunnel

1. Leave the server running
2. Install [ngrok](https://ngrok.com/docs/getting-started/)
3. Open a new terminal tab in the root of the project and run:

```sh
ngrok http 4000
```

4. Now you can find the server address under the “Forwarding” section. You always get a random address on each ngrok execution. Run it once and copy the forwarding address and update the middleware in the `app.py` file and `servers/url` in the `openapi.json`

```python
# ./app.py

app.add_middleware(
CORSMiddleware,
allow_origins=["https://chat.openai.com", "ADDRESS"],
allow_methods=["*"],
allow_headers=["*"],
allow_credentials=True
)

```

```json
# ./openapi.json

...
"servers": [{ "url": "ADDRESS" }],
...
```
