# Base de Conhecimento

## Dados Utilizados

Descreva se usou os arquivos da pasta `data`, por exemplo:

| Arquivo | Formato | Utilização no Agente |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Contextualizar interações anteriores |
| `perfil_investidor.json` | JSON | Personalizar recomendações |
| `produtos_financeiros.json` | JSON | Sugerir produtos adequados ao perfil |
| `transacoes.csv` | CSV | Analisar padrão de gastos do cliente |

> [!TIP]
> **Quer um dataset mais robusto?** Você pode utilizar datasets públicos do [Hugging Face](https://huggingface.co/datasets) relacionados a finanças, desde que sejam adequados ao contexto do desafio.

---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

Os dados não foram modificados. Para que o agente funcione da melhor maneira deveríamos adicionar dados relacionados ao cálculo avançado de risco. 
Coloco meus projetos para inserção de dados. Poderia configurar para que os projetos fossem executados após serem alimentados com os dados de investimento do cliente (outo arquivo).
Cálculo Var de Crédito.ipynb ->https://colab.research.google.com/drive/1DRmJB2VGGZHszwmVrfUE_gNk5AW1gcaP?usp=sharing
Diverdificacao_acao ->https://colab.research.google.com/drive/12VGklZhDkpIj65mvWHgIYPCoUwbRJxU2?usp=sharing
Projeto_VaR_Parametrico ->https://colab.research.google.com/drive/1LI3UMyzYaCENILd4kbVojqwzHtdcMaCk?usp=sharing

Para renda fixa poderia utilizar os arquivos do projeto de especialista de Renda Fixa ->https://notebooklm.google.com/notebook/b10adf54-5978-44fa-b065-bc3699500272
---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.
Os dados poderiam ser carregados no início da sessão, utilizando o contexto dos investimentos e do perfil do investidor para guiar a conversa.


### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

Os dados da pasta  `data` serão carregados e informações de investimento prévios, quando existentes serão utilizados. Assim não será necessário inserir os dados do prompt novamente a cada atualização.

