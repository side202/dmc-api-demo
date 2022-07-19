Api demo with Flask

```
pip install -r requirements.txt
cd src/
export FLASK_APP=api.py
flask run -h 0.0.0.0 -p 8080
```

Prueba:
```
curl localhost:8080/todos/
curl localhost:8080/todos/todo3
```
