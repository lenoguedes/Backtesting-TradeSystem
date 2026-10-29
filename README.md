# Backtest de setup de tendência (Pine Script)

Estratégia em Pine Script v5 para testar no TradingView, com dados históricos, um setup de compra a favor da tendência. O objetivo é medir a regra antes de arriscar dinheiro: taxa de acerto, sequência de perdas e retorno ao longo de muitas operações, e não o resultado de uma semana boa.

## A regra testada

**Filtro de tendência:** só compra quando as três médias exponenciais (9, 21 e 144) estão alinhadas e subindo.

**Gatilhos de entrada:**
- *Inside bar:* candle contido no anterior, com fechamento acima da média de 9.
- *Fundo com reversão:* mínima abaixo das duas anteriores, mas fechamento acima do candle anterior e da média de 9.

**Execução:** ordem de compra stop um tick acima da máxima do candle sinal.

**Saídas:**
- Stop um tick abaixo da mínima do candle sinal.
- Alvo parcial configurável (1x, 1,6x, 2x ou 3x a amplitude do candle sinal).

**Gestão de risco:** o tamanho da posição é calculado para arriscar um percentual fixo do capital atual por operação (parâmetro `Risco Máximo, %`).

## Parâmetros

| Parâmetro | Padrão | Função |
| :--- | :--- | :--- |
| Médias curta, intermediária e longa | 9, 21, 144 | Filtro de tendência |
| Parcial | 1,6 | Alvo em múltiplos da amplitude do candle sinal |
| Risco Máximo, % | 15 | Percentual do capital arriscado por operação |
| Datas de início e fim | 27/02/2022 a 31/12/2030 | Janela do backtest |

## Como usar

1. No TradingView, abra o **Pine Editor**.
2. Cole o conteúdo de `backtest.pine` e clique em **Adicionar ao gráfico**.
3. Veja os resultados na aba **Testador de estratégia** e ajuste os parâmetros nas configurações.

> Projeto de estudo. Não é recomendação de investimento.
