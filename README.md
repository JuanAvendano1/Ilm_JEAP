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
para ver las API en modo no streaming osea,que lo genere de un totazo se usa El siguiente comando:

````bash
curl http://localhost:11434/api/generate -d '{
  "model": "tinyllama",
    "prompt": "Why is the sky blue?",
      "stream": false
      }'
````


