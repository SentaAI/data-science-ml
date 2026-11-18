# SentaAI

Global Solution 2026 (FIAP), Data Science & Statistical Computing. Tema: Citizen Tech.

**Site:** https://senta-ai-sigma.vercel.app/

## A solução

O SentaAI é uma interface instalada na parte externa dos ônibus. Ela usa a catraca e sensores nas portas para estimar a lotação, mostrar assentos livres antes do embarque e identificar entradas irregulares pela porta traseira.

Neste repositório, usamos a base pública de atrasos de ônibus da TTC (Toronto, 2022), porque atrasos são uma das principais causas de superlotação. Comparamos dois modelos distintos para decidir qual se aplica melhor ao painel do SentaAI.

## O que conseguimos

- **Regressão Linear (quanto o ônibus vai atrasar):** erra, em média, cerca de 7 minutos, bem menos que prever sempre a média. Explica cerca de 44% da variação do atraso, o que é esperado, já que clima e trânsito não estão na base.
- **Regressão Logística (o atraso será crítico?):** identifica a grande maioria dos atrasos críticos, com bom poder de separação entre casos críticos e normais (ROC-AUC de 0,88).
- **Modelo mais indicado:** a Regressão Logística, porque decidir se avisa o passageiro é mais útil e mais confiável do que acertar o minuto exato.
- **Regra de negócio:** deixamos o alerta mais sensível, priorizando não deixar passar um ônibus lotado, mesmo com alguns avisos a mais.
- **Principal fator de atraso:** o tipo de incidente, com os desvios de rota no topo.
- **Cuidado com vazamento de dados:** deixamos de fora uma variável que só é conhecida depois do atraso, que inflaria artificialmente os resultados.

O notebook também traz a interpretação dos modelos, uma simulação de cenários no formato do painel e as limitações da base.

## Como abrir

1. Baixe a base de atrasos de 2022 no [Open Data Toronto](https://open.toronto.ca/dataset/ttc-bus-delay-data/) e salve como `ttc-bus-delay-data-2022.csv` **na raiz do projeto**, ao lado do notebook. Sem esse arquivo, o notebook não roda.
2. Instale as bibliotecas: `pip install pandas numpy matplotlib scikit-learn`.
3. Abra [notebook_gs_citizen.ipynb](notebook_gs_citizen.ipynb) no Jupyter ou no VS Code.
4. Execute todas as células. Os modelos são salvos em `modelos/`.

## Integrantes

| Nome | RM |
|:---|:---|
| Arthur Berlofa Bosi | RM564438 |
| Levi de Jesus | RM563279 |
| Luigi Borghi | RM563096 |
| Ulisses Ribeiro | RM562230 |
