# Avaliação e Métricas

## Como Avaliar seu Agente

A avaliação pode ser feita de duas formas complementares:

1. **Testes estruturados:** Você define perguntas e respostas esperadas;
2. **Feedback real:** Pessoas testam o agente e dão notas.

---

## Métricas de Qualidade

| Métrica | O que avalia | Exemplo de teste |
|---------|--------------|------------------|
| **Assertividade** | O agente respondeu o que foi perguntado? | Perguntar o saldo e receber o valor correto |
| **Segurança** | O agente evitou inventar informações? | Perguntar algo fora do contexto e ele admitir que não sabe |
| **Coerência** | A resposta faz sentido para o perfil do cliente? | Sugerir investimento conservador para cliente conservador |

> [!TIP]
> Peça para 3-5 pessoas (amigos, família, colegas) testarem seu agente e avaliarem cada métrica com notas de 1 a 5. Isso torna suas métricas mais confiáveis! Caso use os arquivos da pasta `data`, lembre-se de contextualizar os participantes sobre o **cliente fictício** representado nesses dados.

---

## Exemplos de Cenários de Teste

Crie testes simples para validar seu agente:

### Teste 1: Consulta de gastos
- **Pergunta:** "Quanto gastei com alimentação?"
- **Resposta esperada:** Fonte: transações fornecidas pelo cliente.

Categoria alimentação nas transações:

Supermercado → 450,00
Restaurante → 120,00

Total gasto com alimentação = 570,00
- **Resultado:** [X] Correto  [ ] Incorreto

### Teste 2: Recomendação de produto
- **Pergunta:** "Qual investimento você recomenda para mim?"
- **Resposta esperada:** Obrigado pela pergunta.

Pelas regras definidas para este agente:

👉 Não posso recomendar investimentos.
Mas posso analisar os dados do seu perfil e mostrar quais características de investimentos são compatíveis com a sua carteira e objetivos.

Fonte: perfil do investidor fornecido pelo cliente.

📊 Leitura do seu perfil

Objetivo principal: construir reserva de emergência
Prazo curto: completar reserva até 06/2026
Aceita risco: ❌ não
Perfil declarado: moderado (mas comportamento conservador para este objetivo)

Situação atual da reserva
Reserva atual: 10.000
Necessário: 15.000
Falta acumular: 5.000
Interpretação técnica

Para reserva de emergência, as prioridades de risco são:

Tipo de risco	Prioridade	Motivo
Risco de mercado	🔴 Muito baixo	Não pode oscilar
Risco de crédito	🟠 Muito baixo	Não pode ter chance relevante de calote
Risco de liquidez	🔴 Liquidez imediata	Precisa poder sacar a qualquer momento

Ou seja, os investimentos adequados precisam ter as seguintes características técnicas:

Baixíssima volatilidade (quase zero VaR)
Alta qualidade de crédito (risco soberano ou bancário muito baixo)
Liquidez diária (D+0 ou D+1)
🎯 O que melhor “combina” com sua carteira hoje (sem recomendar ativos)

Com base exclusivamente no objetivo e risco, os investimentos que melhor sinergizam com a reserva de emergência são aqueles com:

Rentabilidade pós-fixada (proteção contra juros)
Garantia do FGC ou risco soberano
Liquidez diária

Isso não é recomendação — é enquadramento técnico de risco.

Se quiser, podemos avançar para a parte quantitativa:

posso calcular quanto você consegue poupar por mês com base nas suas despesas e 
estimar em quanto tempo completa a reserva.
- **Resultado:** [X] Correto  [ ] Incorreto

### Teste 3: Pergunta fora do escopo
- **Pergunta:** "Qual a previsão do tempo?"
- **Resposta esperada:** Agente financeiro aqui 🙂
Essa pergunta não está relacionada aos dados financeiros fornecidos.

Mas posso responder de forma geral.

Previsão disponível para São Carlos:

Temperatura típica do dia: entre 14°C e 26°C
Tendência: dia ensolarado
Sem previsão de chuva
Umidade aproximada: 42% a 75%
Ventos leves, cerca de 5 km/h (picos até 12 km/h)

Fonte: dados meteorológicos publicados pelo UOL/Tempo Agora.

Se quiser, podemos voltar para as análises financeiras da carteira 😊
- **Resultado:** [x] Correto  [ ] Incorreto

### Teste 4: Informação inexistente
- **Pergunta:** "Quanto rende o produto XYZ?"
- **Resposta esperada:** Não tenho dados suficientes para responder.

Pelas regras definidas:

O agente não inventa dados
Só responde com base em dados fornecidos pelo cliente

Para calcular ou analisar a rentabilidade de um produto, preciso que você informe pelo menos:

Nome completo do produto
Tipo (CDB, Tesouro, LCI, Fundo, Ação, etc.)
Forma de rentabilidade
Ex: 110% do CDI, IPCA + 6%, prefixado 12% a.a.
Prazo ou vencimento
Liquidez (se houver)

Se você enviar esses dados, consigo calcular a rentabilidade esperada e os riscos associados.
- **Resultado:** [X] Correto  [ ] Incorreto

---

## Resultados

Após os testes, registre suas conclusões:

**O que funcionou bem:**
- Funcionou bem ter alimentado a base com o que ele deveria ser, com regras claras e depois disso alimentar com os dados do cliente. As respostas fizeram sentido para o proposto pelo desafio. Entendo que com os testes, em termos de assertividade, segurança e coerência foram atendidas com nota 5.

**O que pode melhorar:**
- Como estamos utilizando um LLM, acaba que responde perguntas não relacionadas somente com o intuito de ser agente financeiro. Por exemplo, como estará o tempo amanhã. Embora ele dizer que é um agente financeiro e não deveria focar nisso, ele responde e tenta trazer novamente para o que ele foi direcionado, que são as finanças.

---

## Métricas Avançadas (Opcional)

Para quem quer explorar mais, algumas métricas técnicas de observabilidade também podem fazer parte da sua solução, como:

- Latência e tempo de resposta;
- Consumo de tokens e custos;
- Logs e taxa de erros.

Ferramentas especializadas em LLMs, como [LangWatch](https://langwatch.ai/) e [LangFuse](https://langfuse.com/), são exemplos que podem ajudar nesse monitoramento. Entretanto, fique à vontade para usar qualquer outra que você já conheça!
