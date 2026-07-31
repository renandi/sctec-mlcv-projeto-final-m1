# Análise e Previsão de Evasão de Clientes (Churn) em E-commerce

## Visão Geral do Projeto
Este projeto tem como objetivo analisar o comportamento de clientes em uma plataforma de e-commerce e prever a probabilidade de um cliente deixar de utilizar o serviço (fenômeno conhecido como *Churn*). A identificação antecipada desses usuários permite que a empresa tome ações preventivas, reduzindo a perda de receita e otimizando os custos de retenção.

## Instalação e Configuração
O gerenciamento de pacotes deste projeto foi feito utilizando a ferramenta rápida `uv`. Para configurar o ambiente e instalar as dependências, utilize o comando:

```bash
uv pip install pandas numpy seaborn matplotlib scikit-learn imblearn
```

## Base de Dados e Dicionário de Variáveis
A base de dados utilizada contém diversas informações sobre o histórico e o comportamento dos clientes. 

* **Variável Alvo (Target):**
  * `Churn`: Indica se o cliente abandonou o serviço (1) ou não (0).

* **Principais Variáveis de Perfil e Comportamento:**
  * `Tenure`: Tempo de relacionamento do cliente com a empresa.
  * `CityTier`: Categoria da cidade onde o cliente reside.
  * `WarehouseToHome`: Distância do centro de distribuição até a casa do cliente.
  * `HourSpendOnApp`: Horas gastas no aplicativo móvel ou site.
  * `NumberOfDeviceRegistered`: Número total de dispositivos registrados pelo cliente.
  * `SatisfactionScore`: Nota de satisfação do cliente com o serviço.
  * `Complain`: Indicador se o cliente fez alguma reclamação no último mês.
  * `OrderAmountHikeFromlastYear`: Aumento percentual no valor dos pedidos em relação ao ano anterior.
  * `CouponUsed` / `OrderCount`: Quantidade de cupons utilizados e total de pedidos no último mês.
  * `DaySinceLastOrder`: Dias desde o último pedido do cliente.
  * `CashbackAmount`: Valor médio de cashback recebido no último mês.
  * Informações Categóricas: Aparelho de login preferido, forma de pagamento, gênero, categoria de produtos favorita, estado civil, etc.
  * *Nota: A variável `CustomerID` atua apenas como identificador único e foi desconsiderada para a modelagem.*

## Etapas de Desenvolvimento

**1. Limpeza e Tratamento de Dados**
* Identificação e remoção de registros duplicados (mais de 500 linhas removidas na análise inicial).
* Preenchimento de informações ausentes utilizando valores centrais (como a mediana) para garantir a integridade da análise.
* Mapeamento de valores extremos (outliers) para ajuste fino do escopo de dados.

**2. Engenharia de Funcionalidades (Feature Engineering)**
* Criação de novas perspectivas de análise para enriquecer a modelagem, como o cálculo da proporção de retorno financeiro por compra efetuada (Cashback por Pedido).

**3. Preparação e Balanceamento**
* Separação dos dados em duas partes: uma para ensinar o algoritmo (Treino, 80%) e outra para testá-lo em um cenário que simula a realidade (Teste, 20%).
* Como a grande maioria dos clientes não abandona a plataforma, os dados originais eram desbalanceados. Foi aplicada uma técnica de reamostragem estatística para equilibrar as informações exclusivamente na base de treino, garantindo que a inteligência artificial aprenda a reconhecer o perfil de quem realmente sai.
* Ajuste de escala dos dados numéricos para modelos que dependem do cálculo de distâncias.

**4. Modelagem e Diagnóstico**
* Foram testados algoritmos distintos (como K-Nearest Neighbors e Árvores de Decisão), variando as configurações de complexidade de cada um.
* O objetivo principal dessa fase foi realizar testes rigorosos para evitar que o modelo apenas memorizasse os clientes existentes no treino (fenômeno do *overfitting*), garantindo que ele tenha uma boa capacidade de generalização com clientes novos.

**5. Avaliação e Veredito de Negócios**
* Na perspectiva de negócios, existem dois tipos de erro que o modelo pode cometer:
  * **Falso Positivo:** O modelo acredita que o cliente vai sair, mas ele decide ficar. O custo neste caso é operacional (por exemplo, o custo de enviar um cupom de desconto desnecessário).
  * **Falso Negativo:** O modelo acredita que o cliente vai ficar, mas na verdade ele cancela o serviço. Este impacto financeiro é muito mais grave, pois a empresa perde todo o valor vitalício do cliente (*Lifetime Value*) e precisará investir muito mais (*Custo de Aquisição de Clientes*) para atrair um novo consumidor para o funil de vendas.
* **Conclusão:** Baseado no risco de negócios, o modelo de Árvore de Decisão com profundidade controlada foi validado como o melhor candidato para produção. Ele apresentou a capacidade mais sólida de identificar os clientes com real risco de evasão (minimizando os perigosos falsos negativos) e fornece regras mais claras e interpretáveis para a equipe de negócios atuar.
