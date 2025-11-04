# 📊 CRM Analytics — Painel de Indicadores de Relacionamento com Clientes  

> **Autor:** Jorge Gabriel  
> **Ferramentas:** Google Sheets | Looker Studio  
> **Técnicas:** Segmentação RFM | Análise de Churn | LTV | Pareto | CRM Analytics  
> **Fonte de Dados:** [Customer Personality Analysis (Kaggle)](https://www.kaggle.com/datasets/imakash3011/customer-personality-analysis)

---

## 🧭 Descrição do Projeto  

O **CRM Analytics** é um painel interativo desenvolvido para analisar o comportamento e o valor de clientes, aplicando técnicas de **segmentação RFM (Recência, Frequência e Valor Monetário)** e indicadores de **retenção (Churn)** e **valor vitalício (LTV)**.  

O objetivo é demonstrar como métricas de CRM podem orientar **estratégias de fidelização, cross-sell e otimização de campanhas de marketing**.  
O projeto utiliza uma abordagem **low-code**, baseada em Google Sheets e Looker Studio.

---

## 🎯 Objetivos Analíticos  

- Segmentar clientes com base em comportamento de compra (RFM);  
- Identificar perfis de maior valor e risco de churn;  
- Mapear produtos e canais que concentram receita;  
- Apoiar campanhas de fidelização e estratégias de cross-sell/upsell;  
- Avaliar o impacto das campanhas de marketing e evolução da base de clientes.  

---

## 🧩 Fonte de Dados  

**Dataset:** *Customer Personality Analysis*  
**Origem:** [Kaggle – Customer Personality Analysis](https://www.kaggle.com/datasets/imakash3011/customer-personality-analysis)  
**Descrição:** Base com dados demográficos, comportamentais e financeiros de clientes de uma empresa de vendas diretas, cobrindo dois anos de histórico de interações.  

---

## ⚙️ Pipeline de Dados  

### 1️⃣ Coleta e Ingestão  
- Download do dataset `.csv`;  
- Upload para o Google Drive e conexão ao **Google Sheets**;  
- Estruturação em camadas:  
  - 🟤 **Bronze:** dados brutos;  
  - ⚪ **Silver:** dados curados e traduzidos;  
  - 🟡 **Gold:** dados refinados com colunas derivadas e métricas agregadas.  

### 2️⃣ Limpeza e Tratamento  
- Padronização de separadores decimais (vírgula → ponto);  
- Tradução das colunas para português;  
- Conversão da renda anual em **renda familiar mensal** (base IPEA);  
- Normalização de variáveis de data e criação de faixas etárias e de renda;  
- Manutenção de registros com *missing values* não críticos.  

### 3️⃣ Modelagem e Enriquecimento  
Criação de colunas derivadas na camada *gold*:  

| Categoria | Coluna Derivada | Descrição |
|------------|-----------------|------------|
| Demográfica | `Idade`, `Faixa_Etaria` | Cálculo e categorização por faixa de 10 anos |
| Financeira | `Renda_Mensal_Domiciliar`, `Faixa_Renda (IPEA)` | Conversão e categorização conforme metodologia IPEA |
| Familiar | `Num_Pessoas_Familia` | Cliente + dependentes |
| Financeira | `Total_Gasto`, `Num_Total_Compras` | Soma de gastos e compras em todos os canais |
| RFM | `R_Score`, `F_Score`, `M_Score`, `Segmento_RFM` | Distribuição em quintis e classificação conforme matriz de segmentação |
| Pareto | `Gasto_Acumulado`, `%_Gasto_Acumulado`, `Cliente_Pareto` | Identificação dos 80% principais clientes |
| Retenção | `Churn_Flag` | Clientes em risco (1) e ativos (0) |
| Temporal | `Data_Snapshot`, `Data_Ultima_Compra`, `Tempo_Permanencia_Anos` | Medidas de permanência e recência |

---

## 📊 Métricas Principais  

- **RFM Scores:** Recência, Frequência e Monetário  
- **Ticket Médio e Faturamento Total por Segmento**  
- **LTV Mediano (Life Time Value)**  
- **% de Clientes em Risco de Churn**  
- **Distribuição de Receita por Produto e Canal de Venda**  
- **Taxa de Resposta às Campanhas de Marketing**

---

## 🧭 Estrutura do Dashboard  

O painel foi construído no **Looker Studio** e organizado em 5 seções:  

| Seção | Foco Analítico |  
|--------|----------------|  
| **Visão Geral** | Indicadores macro do CRM (clientes, receita, ticket médio, RFM) |  
| **Produto** | Análise de mix, desempenho e comportamento de compra |  
| **Cliente** | Perfis demográficos e segmentação RFM detalhada |  
| **Canal de Vendas** | Comparação entre loja física, web e catálogo |  
| **LTV & Churn** | Valor vitalício e risco de inativação (churn) |  

---

## 🔍 Principais Insights  

- 💰 **38% dos clientes** concentram **80% da receita**, principalmente nos segmentos *Fiéis*, *Campeões* e *Em Risco*;  
- ⚠️ **24% da base** está em risco de churn, representando **19,8% do faturamento total**;  
- 🍷 **Vinhos e carnes** respondem por **78% da receita**, indicando dependência de portfólio;  
- 📈 **O LTV mediano dos Campeões (R$ 33,6 mil)** é **3x maior** que o dos demais segmentos;  
- 👥 Análises demográficas mostram que **clientes de vinhos** têm **maior renda e escolaridade**, enquanto **consumidores de carnes** concentram-se em **faixas etárias mais jovens** — insights úteis para campanhas segmentadas;  
- 📣 Campanhas de marketing têm **6% de taxa média de resposta**, reforçando a importância da personalização.  

---

## 🧠 Conclusão  

O projeto demonstra o uso de **CRM Analytics** como ferramenta estratégica para **decisões orientadas por dados**, unindo comportamento do cliente e métricas de valor.  
Mesmo com um pipeline **low-code**, foi possível entregar uma análise robusta de **retenção, engajamento e valor do cliente**.  

---

## 🧩 Aprendizados e Próximos Passos  

**Aprendizados-chave:**  
- Planejar e documentar um pipeline completo é tão importante quanto visualizar resultados;  
- A modelagem RFM traduz com precisão o comportamento de compra e o potencial de fidelização;  
- Dashboards só geram valor quando contam uma história clara para o negócio;  
- Mesmo ferramentas simples (Sheets + Looker) podem entregar análises profissionais, se bem estruturadas.  

**Próximos passos:**  
- Reproduzir o projeto em **Python e SQL**, com foco em escalabilidade e automação;  
- Implementar **clustering (K-Means)** para comparar com a segmentação RFM;  
- Construir uma versão em **Power BI** com previsões de churn via machine learning leve;  
- Aplicar o mesmo raciocínio de CRM Analytics em **contextos de pós-venda e fidelização**.  

> Este projeto representa um estudo aplicado de CRM Analytics com foco em traduzir comportamento de clientes em insights acionáveis para o negócio.

---

## 🔗 Links  

- 📊 **Dashboard no Looker Studio:** *[https://lookerstudio.google.com/reporting/75530da3-0949-4bfa-816f-a2fb3957ce50/page/T7TTF]*  
- 🗂️ **Repositório / README técnico:** *[https://docs.google.com/document/d/1vFbAXWpYxHcFy8zaWcXeysCU1twqRpX1LdbpzgMLH4w/edit?tab=t.0]*  
- 💾 **Fonte dos Dados:** [Kaggle Dataset](https://www.kaggle.com/datasets/imakash3011/customer-personality-analysis)

---

## ⚖️ Licença  
Este projeto é distribuído sob a licença [MIT](LICENSE).

---
