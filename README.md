# Tech Challenge Fase 1 - Análise e Estratégia de NPS em E-commerce

Repositório desenvolvido para a entrega do Tech Challenge da Fase 1 (Pós Tech). O projeto analisa dados operacionais e de atendimento de um e-commerce nacional para identificar os principais fatores que geram clientes detratores e propor ações preventivas antes da coleta da pesquisa de satisfaçã.

## 1. Objetivo do Projeto
Com o aumento no volume de vendas do e-commerce, a empresa passou a registrar uma forte queda e variabilidade no seu Net Promoter Score (NPS), acumulando 84,4% de clientes detratores (nota menor que 7,0) e uma média geral de 4,38. Como a pesquisa de NPS só é aplicada após o fim da jornada de compra, a operação atua hoje de forma reativa.

O objetivo deste trabalho é:
- Mapear quais etapas da operação (pedido, logística ou atendimento) mais impactam a nota do cliente;
- Identificar os "pontos de ruptura" na jornada que transformam consumidores em detratores;
- Avaliar o impacto direto do NPS na taxa de recompra em 30 dias;

## 2. Descrição da Base de Dados
A base histórica (`data/desafio_nps_fase_1.csv`) possui 2.500 registros de pedidos e 19 colunas, sem valores ausentes:

- **Dados do Cliente:** `customer_id`, `customer_age` (idade), `customer_region` (região geográfica) e `customer_tenure_months` (tempo de relacionamento em meses).
- **Dados do Pedido:** `order_id`, `order_value` (valor total), `items_quantity` (quantidade de itens), `discount_value` (desconto aplicado) e `payment_installments` (parcelas).
- **Dados Logísticos:** `delivery_time_days` (prazo total de entrega), `delivery_delay_days` (dias de atraso além do combinado), `freight_value` (valor do frete) e `delivery_attempts` (tentativas de entrega).
- **Dados de Atendimento (SAC):** `customer_service_contacts` (contatos com o suporte), `resolution_time_days` (tempo para resolução de problemas em dias) e `complaints_count` (quantidade de reclamações registradas).
- **Indicadores de Satisfação e Negócio:** `nps_score` (nota de 0 a 10 coletada após a compra — variável alvo), `csat_internal_score` (score interno) e `repeat_purchase_30d` (indica se houve recompra em até 30 dias: 0 = não, 1 = sim).

## 3. Metodologia Utilizada
O estudo foi dividido em quatro etapas principais dentro do notebook principal (`notebooks/`):
1. **Entendimento do Negócio:** Diagnóstico do cenário do e-commerce, relação financeira entre NPS e retenção (CAC vs. Recompra) e mapeamento das áreas impactadas (Logística, SAC, Produto e CRM).
2. **Definição Conceitual da Target:** Análise da variável `nps_score`, segmentação nas faixas de mercado (Detratores `< 7,0`, Neutros `7,0 a 8,9` e Promotores `>= 9,0`) e avaliação dos riscos de vazamento de dados (*data leakage*) com variáveis pós-compra].
3. **Análise Exploratória de Dados (EDA):** Cruzamento estatístico e visual das variáveis operacionais e demográficas para isolar os reais ofensores da satisfação e encontrar os limites de tolerância do cliente.
4. **Estratégia Preditiva:** Comparação técnica e executiva entre abordagens de Regressão e Classificação para antecipação de risco na operação.
