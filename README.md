# Abaqus-Python-3.7-Interface
Interface entre python 3.7 e abaqus

## 1- Instalar dependências:
- Scipy -> Python 3.7
- PyZMQ -> Python 3.7 + Abaqus (Python 2.7)
com:\
<code>abaqus-python-addpkg.py install --conda PyZMQ</code>

## 2-Criar Cliente e Servidor Local.

Servidor:
```python
    import zmq
    context = zmq.Context()
    socket = context.socket(zmq.REP)
    socket.bind('tcp://*:5555')
```
Cliente:
```python
    import zmq
    context = zmq.Context()
    socket = context.socket(zmq.REQ)
    socket.connect('tcp://localhost:5555')
```
### 2.1 Enviar e receber Objetos:
```python
    socket.send_pyobj(obj) #Enviar Obj:
    
    obj = socket.recv_pyobj() #Receber Obj
```
A função que recebe espera até algum objeto ser executado. Sempre que enviar, deve-se antes receber para poder enviar de novo. O mesmo para receber.



