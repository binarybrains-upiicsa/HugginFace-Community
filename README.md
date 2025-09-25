# HugginFace-Community
Se detallarán los pasos para unirse a la comunidad de Hugging Face 🤗 y las primeras acciones para aprender a navegar en la plataforma.

Únete a nuestra gran Comunidad de Hugging Face donde estaremos creando, desarrollando y experimentando con modelos de Fundacionales, Machine Learning y Deep Learning!

[Únete a la Comunidad 🤗💙](https://huggingface.co/BinaryBrainsAI)  
<details>
  <summary><strong>Generación de tokens en Hugging Face 🤗</strong></summary>

  Con la ayuda de un feature llamado **Serverless API**, nos permitirá usar modelos directamente desde la nube de Hugging Face 🤗 solo con tu token, sin necesidad de instalar librerías, descargar pesos o desplegar entornos.  
  Además, este token nos dará acceso a funcionalidades adicionales como:

  * Descargar modelos privados o con licencia restringida.  
  * Subir y gestionar nuestros propios modelos y datasets en el Hub.  

  ### Instrucciones 
  * Entraremos a [Hugging Face](https://huggingface.co/)  
  * Daremos permisos de lectura a nuestro token  
![478645250-5b62c83b-b616-442b-ae8f-420a3dc1e311](https://github.com/user-attachments/assets/32036ef0-537f-4ed8-b785-5f2c72d471bd)

</details>

<details>
  <summary><strong>Uso de LLM's en Hugging Face 🤗</strong></summary>
  Haremos uso de nuestro token generado en HF 🤗 para poder hacer uso de los modelos que se encuentran aquí.

  En tu terminal, instala el Hugging Face Hub Python client y haz log in:

```shell
pip install huggingface_hub
hf auth login
```

   Una vez ejecutes el  *hf auth login*   tendrás que pegar tu TOKEN generado anteriormente para logearte y poder hacer uso de el en tu código :

![Untitled](https://github.com/user-attachments/assets/77e601fe-ec66-4471-907f-0fc628776fa2)

### Python

   ```python
import os
from huggingface_hub import InferenceClient

client = InferenceClient()

completion = client.chat.completions.create(
    model="openai/gpt-oss-120b",
    messages=[
        {
            "role": "user",
            "content": "How many 'G's in 'huggingface'?"
        }
    ],
)

print(completion.choices[0].message)

```

Aquí esta otra forma en la cual agregamos el TOKEN  en forma de variable en nuestro código:

   ```python
import os
from huggingface_hub import InferenceClient

os.environ["HF_TOKEN"] = "TU_TOKEN_AQUI"

client = InferenceClient("google/gemma-2-2b-it", token=os.environ["HF_TOKEN"])

resp = client.chat_completion(
    messages=[{"role": "user",
               "content": "Escribe un poema sobre un gato y un perro que son amigos"}],
    max_tokens=120,
    temperature=0.7,
)

print(resp.choices[0].message["content"])

```

### JavaScript

```shell
npm install @huggingface/inference
```


```shell
import { InferenceClient } from "@huggingface/inference";

const client = new InferenceClient(process.env.HF_TOKEN);

const chatCompletion = await client.chatCompletion({
  model: "deepseek-ai/DeepSeek-V3-0324",
  messages: [
    {
      role: "user",
      content: "How many 'G's in 'huggingface'?",
    },
  ],
});

console.log(chatCompletion.choices[0].message);
```


Podrás seleccionar distintos tipos de modelos los cuales podrás encontrarlos en el Hub de Hugging Face [Hugging Face Models](https://huggingface.co/models)  🤗

<img width="1905" height="926" alt="image" src="https://github.com/user-attachments/assets/66fb3791-08b8-4cfc-9c17-aa1c0b25e5ad" />

Así mismo vas a poder encontrar modelos que se puedan ajustar mejor a cada tipo de tarea que tu necesites

<img width="465" height="303" alt="image" src="https://github.com/user-attachments/assets/d535c7b6-38bf-49cb-9c54-47e3b23c136d" />


</details>
