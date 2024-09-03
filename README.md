# Ilm_JEAP
Repositorio de prueba para implementar LLM y una aplicacion web
# LLM pruebas

# 1. Instalación 

Cómo primer paso descargamos [ollama](https://ollama.com/download/linux) de si página web, y ejecutamos el siguiente comando:

````bash
$ curl -fsSL https://ollama.com/install.sh |sh
````

## 2.Arrancar el servidor 
Se arranca el servidor de ollama rest con el siguiente comando:

Nota:primero se carga el servidory después se abre otra consola para empezara cargar las API y empezar a preguntar
````bash
$ ollama serve
````
## 3. vamosa descargar un modelo de [ollama list](https://ollama.com/library)
utilizando el siguiente comando:

````bash
$ ollama pull tinyllama 
````

## 4.ver API REST en modo streaming
para ver APIS en ollama en modo streaming para para que lo vaya generando se usa el siguiente comando:
"La parte de salida.md es para guardar lo que genera el comando ".
````bash
curl http://localhost:11434/api/generate -d '{
  "model": "tinyllama",
    "prompt": "Why is the sky blue?"
    }' -o salida.md
````
## 4.1 Para verlo en modo no streaming 
para ver las API en modo no streaming osea,que lo genere de un totazo se usa El siguiente comando:git commit -m "UPDATED README.md"

````bash
curl http://localhost:11434/api/generate -d '{
  "model": "tinyllama",
    "prompt": "Why is the sky blue?",
      "stream": false
      }'
````

## 5. para guardar en GitHub
Para actualizar en GitHub se puede de 3 maneras:

git add .

git commit -m "UPDATED README.md"

git push -u origin main$ curl -fsSL https://ollama.com/install.sh |sh

## 6. Para copiar una api key de groq
Primero vamos a ingresar a groq por el siguiente link
[groq](https://console.groq.com)
Ingresamos con el usuario de github y vamos a la parte de api keys
Creamos un api key, copiamos el api key en un bloc de notas y usamos el siguiente comando en ollama:

````bash
curl "https://api.groq.com/openai/v1/chat/completions" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer ${GROQ_API_KEY}" \
  -d '{
         "messages": [
           {
             "role": "user",
             "content": "¿Por que el cielo es azul?"
           }
         ],
         "model": "llama3-8b-8192",
         "stream": false
       }'
````
## 7. Ejecutar el codigo de PYTHON
Para ejecutar el codigo desde Python se usa este codigo

````bash
import requests

url = 'https://www.w3schools.com/python/demopage.php'
myobj = {'somekey': 'somevalue'}

x = requests.post(url, json = myobj)

print(x.text)
````
Se cambia la URL por la de alguno de los modelos de lenguaje largo que tengamos
Luego se cambia el contenido que esta en las llaves por los parametros que le queramos poner a nuestro codigo
El stream se cambia el "false" por "False" si no se cambia nos genera un error
Queda algo asi:

````bash
import requests

url = 'http://localhost:11434/api/generate'
myobj = {"model": "tinyllama",
    "prompt": "Why is the sky blue?",
      "stream": False
}

x = requests.post(url, json = myobj)

print(x.text)
````