# Codigos-Scripts-Docker-Python
 
 Para realizar a criação da imagem do container em docker, realizei a isntalação do Docker Desktop e do Visual Studio Code(VSCODE).
 
 No Github Desktop ( Que já tinha previamente instalado), criei um repositório para armazenar os arquivos Dockerfile e o script da aplicação em python.
 
 Abri o repositório no Vscode através do Github:
 
 ![image](https://user-images.githubusercontent.com/103289195/163656249-1efdb72c-621b-4dd8-ac0d-556374f4667b.png)

 No VScode , criei os arquivo Olacloudopss.py e o arquivo Dockerfile:

**Olacloudopss.py**

``` 
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello():
    return "Olá, CloudOpss!! )"

if __name__ == "__main__":
    app.run(host="0.0.0.0")
```

No script acima, realizamos a importação do Flask e definimos o que será mostrado na tela da aplicação

**Dockerfile**

```
FROM python:3.10.4
RUN pip install flask
COPY Olacloudopss.py /app.py
CMD ["python","app.py"]
```
No dockerfile, utilizamos a imagem do Python como base e realizamos a instalação do Flask.

Para gerar a imagem do container, executamos o seguinte comando:
` docker image build -t python-docker-co .`

Nota se que o `.` se refere ao diretório no qual estão os arquivos Dockerfile e Olacloudopss.py

Após gerar a imagem do container, executamos o comando: `docker run -p 5001:5000 -d python-docker-co`

No comando acima, determinamos em qual porta o container irá executar `-p 5001:5000` e também fazemos com que o mesmo rode em modo "detached" `-d` 
 
Acessando o navegador com a url "Localhost:5001" , iremos verificar o funcionamento da aplicação.

![image](https://user-images.githubusercontent.com/103289195/163656791-534b7131-7669-48cf-a65d-704abf2ad62a.png).


Para acessar a imagem do container, deve se executar o comando `docker run python-docker-co`, em primeiro momento será realizado o download da mesma.



 
