# Desafio de Projeto - Santander Bootcamp 2023

## Entendendo o desafio
Agora é a sua hora de brilhar e construir um perfil de destaque na DIO! Explore todos os conceitos explorados até aqui e replique (ou melhore, porque não?) este projeto prático. Para isso, crie seu próprio repositório e aumente ainda mais seu portfólio de projetos no GitHub, o qual pode fazer toda diferença em suas entrevistas técnicas 😎

Vocês já mergulharam a fundo no mundo da Ciência de Dados conosco! Juntos, construímos um pipeline ETL eficaz, começando com a simples extração de IDs de usuários de uma planilha, seguindo para uma transformação inovadora com a IA do GPT-4 da OpenAI, e culminando no carregamento desses dados transformados de volta ao 'Santander Dev Week 2023'. Agora, o desafio é reimaginar esse processo de ETL. Como vocês aplicariam o que aprenderam em um novo domínio de aplicação, sem depender diretamente de APIs externas (caso queiram simplificar)? Pensem nas infinitas possibilidades e domínios que podem ser explorados, e deixem a criatividade fluir!



## Ferramentas Utilizadas
[Colab](https://colab.google/) > O Google Colaboratory, carinhosamente chamado de Colab, é um serviço de nuvem gratuito hospedado pelo próprio Google para incentivar a pesquisa de Aprendizado de Máquina e Inteligência Artificial.

[Swagger](https://sdw-2023-prd.up.railway.app/swagger-ui.html) > Swagger: é um conjunto de ferramentas para desenvolvedores de API da SmartBear Software e uma especificação anterior na qual a especificação OpenAPI é baseada.


# Passo-a-passo

## Criando os usuários 
(repetir esses passos para criar todos os usuários)

1º Acessar a [Api Swagger](https://sdw-2023-prd.up.railway.app/swagger-ui/index.html);

2º Clicar em [POST] e depois em [Try Out];

3º Definir as informações do usuario (principalmente nome, conta, cartão e limite) e depois clicar em [Execute]

## Criar Arquivo [sdw2023.csv]
Esse arquivo armazenará as Ids dos usuarios que foram criados, ele poderá ser criado no Bloco de Notas, o importante é salva-lo como ".CSV"

![Exemplo do arquivo .CSV](https://github.com/lilidoferrer/desafio_de_projeto_santander_bootcamp_2023/blob/main/img1.png)

## Programação
Para fazer a implementação a ferramenta utilizada é o Colab.

1º Indicar endereço da API do Swagger
```bash
sdw_url = 'https://sdw-2023-prd.up.railway.app'
```

2º Impostar ids dos clientes do arquivo ".CSV"
import pandas as pd
```bash
df = pd.read_csv('sdw2023.csv')
user_ids = df['UserID'].tolist()
print(user_ids)
```

3º Buscar as informações dos clientes (baseado nas ids do arquivo CSV), na api do Swagger
```bash
from IPython.utils.text import indent
import requests
import json

def get_user(id):
  response = requests.get(f'{sdw_url}/users/{id}')
  return response.json() if response.status_code == 200 else None

users = [user for id in user_ids if(user := get_user(id)) is not None]
print(json.dumps(users , indent=2))
```
4º Instalar a biblioteca openai
```bash
!pip install openai
```
5º Autenticar o uso do chat-GPT, atraves da chave de autenticação
```bash
openai_api_key = 'SUA-CHAVE'
```

6º Criar a "comunicação" entre o Chat_GPT e o programa desenvolvido
```bash
import os
import openai

# Load your API key from an environment variable or secret management service
openai.api_key = openai_api_key

def generate_ia_news(user):
  completion = openai.ChatCompletion.create(
      model="gpt-3.5-turbo",
      messages=[
          {"role": "system", "content": "Ola! Voce é um especialista em marketing bancario!"},
          {"role": "user", "content": f"Voce poderia criar uma mensagem para  {user['name']} sobre a importancia dos investimentos (no maximo 100 caracteres), lembrando a ele que ele possui {user['account']} de limite "},

          ]
      )
  return completion.choices[0].message.content.strip('\n"')

for  user in users:
  news = generate_ia_news(user)
  print(news)
  user['news'].append({
      "icon": "https://digitalinnovationone.github.io/santander-dev-week-2023-api/icons/credit.svg",
      "description": news

  })
```

7º Salvar as mensagens criadas, na api Swagger

```bash
def updade_user(user):
    response = requests.put(f"{sdw_url}/users/{user['id']}", json=user)
    return True if response.status_code == 200 else False

for user in  users:
  sucess = updade_user(user)
  print(f"User {user['name']} atualizado? {sucess}!")
```





## Links Uteis
[colab.research.google.com](colab.research.google.com): Link do Notebook criado via Google Colab com todo o código-fonte desenvolvido neste Desafio de Projeto (Lab);

[github.com/digitalinnovationone/santander-dev-week-2023-api](github.com/digitalinnovationone/santander-dev-week-2023-api: ): GitHub com a API desenvolvida para a Santander Dev Week 2023 com informações úteis (incluindo o link do Swagger e dados importantes sobre a disponibilidade da API). Relevante para quem quiser saber mais sobre o processo de criação da API RESTful consumi neste Lab.

[Documentação Api Chat-GPT](https://platform.openai.com/docs/libraries/python-library)




