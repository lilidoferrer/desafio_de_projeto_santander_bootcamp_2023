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
Esse arquivo armazenará a Id dos usuarios que foram criados



## Programação
Para fazer a implementação a ferramenta utilizada é o Colab.

```bash
pip install foobar
```

## Usage

```python
import foobar

# returns 'words'
foobar.pluralize('word')

# returns 'geese'
foobar.pluralize('goose')

# returns 'phenomenon'
foobar.singularize('phenomena')
```

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.



## Links Uteis
[colab.research.google.com](colab.research.google.com): Link do Notebook criado via Google Colab com todo o código-fonte desenvolvido neste Desafio de Projeto (Lab);

[github.com/digitalinnovationone/santander-dev-week-2023-api](github.com/digitalinnovationone/santander-dev-week-2023-api: ): GitHub com a API desenvolvida para a Santander Dev Week 2023 com informações úteis (incluindo o link do Swagger e dados importantes sobre a disponibilidade da API). Relevante para quem quiser saber mais sobre o processo de criação da API RESTful consumi neste Lab.

[Documentação Api Chat-GPT](https://platform.openai.com/docs/libraries/python-library)




