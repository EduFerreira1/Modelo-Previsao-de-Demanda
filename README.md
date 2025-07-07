# Modelo de Previsão de Demanda com Segmentação de Modelo por Loja (Varejo Supermercadista)

<p align="center">
  <img src="/Images/capa-previsao-demanda.png" width="500"/>
</p>

## Descrição do Projeto

Este projeto tem como objetivo desenvolver e comparar modelos de previsão de demanda para uma grande rede supermercadista, utilizando diferentes abordagens de machine learning. O foco está em substituir o modelo preditivo vigente por soluções mais performáticas, capazes de prever a demanda de milhares de produtos em diferentes lojas para os próximos 15 dias. O projeto aborda desde a criação dos modelos, tunagem de hiperparâmetros, segmentação por loja/perfil e análise financeira do impacto das previsões.

## Motivação

A previsão precisa da demanda é crucial para o planejamento estratégico e operacional do varejo. Previsões equivocadas podem gerar excesso de estoque (impactando custos e perdas com produtos perecíveis) ou ruptura de estoque (resultando em perda de receita e insatisfação do cliente). Uma solução robusta e segmentada traz ganhos diretos para o negócio: aumenta a eficiência, reduz custos e melhora o atendimento ao cliente.

## Conjunto de Dados

### Contexto

O projeto utiliza dados reais de uma rede de supermercados (SuperPoD), incluindo histórico de vendas, promoções, transações, preços, eventos sazonais e dados externos como preços do petróleo. As variáveis-chave abrangem diferentes granularidades (produto, loja, data) e aspectos do negócio (demanda, promoções, feriados, etc).
Atualmente, eles dependem de métodos de previsão utilizando pouquíssimos dados como insumo além de pouca automação para executar os planos. Dessa forma, a SuperPoD gostaria de substituir o modelo preditivo vigente por outro mais performático visando ter previsões com maior precisão. O modelo deve ser capaz de prever a demanda dos próximos 15 dias.

### Fonte dos Dados

Os dados foram disponibilizados pela rede SuperPoD para fins de desenvolvimento de modelos preditivos e estudo de caso.

## Inspiração

O projeto é inspirado por desafios reais enfrentados pelo varejo: adaptar-se rapidamente a diferentes perfis de lojas, sazonalidades e tendências do consumidor. A busca por previsões mais precisas é motivada por ganhos operacionais, competitivos e financeiros, baseando-se em práticas modernas de ciência de dados.

## Principais Técnicas e Algoritmos Utilizados

<p align="center">
  <img src="/Images/crisp-dm.png" width="500"/>
</p>

- **Framework:** CRISP-DM para organização do ciclo do projeto.
- **Bibliotecas:** Pandas, Numpy, Scikit-learn, LightGBM, XGBoost.
- **Modelos treinados:** Regressão Linear, Árvore de Decisão, Random Forest, XGBoost, LightGBM, Modelos Segmentados.
- **Otimização:** Grid Search, Random Search para tunagem de hiperparâmetros.
- **Avaliação:** MAE, MSE, RMSE e avaliação financeira do impacto das previsões.

## Estrutura do Projeto

1. **Entendimento do Negócio**
   - Compreensão dos objetivos, desafios e impacto da previsão de demanda no varejo.
   - Identificação do público-alvo, critérios de sucesso e restrições do projeto.

2. **Entendimento dos Dados**
   - Levantamento e análise exploratória das fontes de dados.
   - Testes de sanidade das variáveis, análise de missing, outliers, granularidade e periodicidade.
     [Acesse o código dessa etapa aqui](01%EDA/Exploratory%Data%Analysis%-%EDA.ipynb)

3. **Preparação dos Dados**    
     [Acesse o código das etapas 3 e 4 aqui](02%Data%Preparation/Data%Preparation.ipynb)
   - Ajuste de tipos de variáveis, joins entre bases, padronização e criação de variáveis derivadas.
   - Filtragem, tratamento de nulos e splits em bases de treino/teste.

4. **Feature Engineering e Seleção de Variáveis**
   - Geração de novas features (lags, rolling, médias móveis, flags sazonais, etc).
   - Seleção de variáveis relevantes usando feature importance e testes estatísticos.

5. **Modelagem**
     [Acesse o código das etapas 5 e 6 aqui](03%Modeling/Modeling.ipynb)
   - Treinamento de diferentes algoritmos para previsão de demanda.
   - Tunagem de hiperparâmetros e comparação de performance.
   - Modelagem segmentada por loja, cluster ou perfil, quando aplicável.

6. **Avaliação dos Modelos**
   - Avaliação das previsões por métricas técnicas (MAE, MSE, RMSE).
   - Análise do comportamento em diferentes lojas, produtos e períodos.
   - Escolha do modelo campeão com base em desempenho técnico e aderência ao negócio.

7. **Segmentação de Modelos**
    [Acesse o código dessa etapa aqui](04%Model%Segmentation%by%Store/Segmentação_de_modelos.ipynb)
   - Aplicação de técnicas de segmentação (demográfica, geográfica, comportamental, valor do cliente).
   - Criação de modelos específicos para cada segmento ou uso de variáveis de segmentação em modelos globais.
   - Análise de custo-benefício entre modelos globais e segmentados.

8. **Avaliação Financeira**
   [Acesse o código dessa etapa aqui](05%Financial%Analysis/Avaliação_financeira.ipynb)
   - Estudo do impacto financeiro das previsões: redução de perdas, ruptura de estoque, aumento de receita e eficiência operacional.
   - Comparação entre modelo vigente e novos modelos propostos sob o ponto de vista financeiro.


## Resultados

A segmentação dos modelos proporcionou ganhos concretos na acurácia da previsão de demanda, conforme demonstrado pelas métricas de erro (RMSE e MAE). O quadro abaixo ilustra a comparação entre o modelo vigente, único (global) e o modelo segmentado:

<div align="center">

| Modelo     | RMSE       | MAE       |
|------------|------------|-----------|
| Vigente    | 10910.38   | 3287.10   |
| Único      | 1004.21    | 442.21    |
| Segmentado | 916.83     | 417.79    |

</div>

> O modelo segmentado trouxe uma redução de aproximadamente **9% no RMSE e 6% no MAE** em relação ao modelo único, tornando as previsões mais ajustadas à realidade operacional de cada loja.

---

No comparativo financeiro final, a soma dos custos de excesso e ruptura mostra o valor trazido pelo modelo segmentado:

<div align="center">

| Modelo           | Custo Total (R$)   |
|------------------|-------------------|
| Modelo Vigente   | 893.437.295,27     |
| Modelo Único     | 73.085.864,41     |
| Segmentado       | 72.220.197,77    |

</div>

> O modelo segmentado proporcionou uma economia superior a **91%** em relação ao modelo vigente, e pouco mais de **1%** frente ao modelo único, representando uma redução de custos de mais de milhões de reais em um ciclo de previsão.

---

---

## Discussão

Os resultados evidenciam que a segmentação de modelos, adaptando-os às particularidades de cada loja, eleva significativamente a assertividade das previsões e, principalmente, gera impacto financeiro relevante para o negócio. A redução nos custos totais de estoque e ruptura demonstra que a ciência de dados pode ir além das métricas técnicas, agregando valor tangível à operação varejista.

Além da acurácia, a abordagem segmentada facilita tomadas de decisão localizadas, tornando o planejamento mais aderente ao contexto real de cada unidade. Entretanto, destaca-se que a maior granularidade exige atenção à manutenção e monitoramento dos modelos, para evitar sobreajuste e garantir ganhos sustentáveis no longo prazo.

Por fim, a análise financeira foi fundamental para conectar o resultado do projeto com o ROI esperado pelo negócio, mostrando que iniciativas de machine learning devem sempre ser acompanhadas de mensuração prática do impacto econômico.


## Próximos Passos

- Automatizar o pipeline de escoragem para produção.
- Implementar dashboards para acompanhamento em tempo real.
- Explorar novas fontes de dados (ex: clima, dados macroeconômicos).
- Evoluir a granularidade da previsão (SKU por canal/loja).
- Refinar as análises financeiras para novas estratégias comerciais.

## Contato

Para dúvidas, sugestões ou colaboração, entre em contato:
- [LinkedIn](https://www.linkedin.com/in/eduferreiraa)
- Email: contatoedu.fsg@gmail.com

---

> Este projeto segue as melhores práticas de ciência de dados aplicadas ao contexto real do varejo, sempre alinhando soluções técnicas com o impacto financeiro e estratégico para o negócio.
