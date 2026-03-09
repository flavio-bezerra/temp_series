# 🔮 Projeto CVC Lojas: Previsão Inteligente de Vendas

Bem-vindo ao **Cérebro Digital de Vendas** da CVC Lojas.

Este documento foi escrito para explicar, de forma simples e didática, como utilizamos Inteligência Artificial para antecipar o futuro das vendas em nossas lojas físicas.

---

## 🎯 O Que é Este Projeto?

Imagine se pudéssemos saber, com antecedência, quanto cada loja da CVC vai vender no próximo mês. Isso nos ajudaria a:
1.  **Definir Metas Justas**: Baseadas no potencial real de cada loja.
2.  **Planejar Campanhas**: Saber onde investir mais marketing.
3.  **Antecipar Problemas**: Identificar lojas que precisão de ajuda antes mesmo do mês começar.

Este projeto é exatamente isso: uma série de "robôs" (algoritmos) que analisam o passado para prever o futuro.

---

## 💡 Como Funciona a "Mágica"? (Sem "Technês")

Para ensinar um computador a prever vendas, nós seguimos um processo que se parece muito com treinar um novo funcionário. Veja a analogia:

### 1. O Estudante (Ingestão de Dados)
Primeiro, o computador precisa estudar. Nós alimentamos ele com **anos de histórico de vendas**, mais informações extras como:
*   Feriados (Carnaval vende menos? Natal vende mais?)
*   Economia (O Dólar subiu? A inflação desceu?)
*   Promoções antigas.

### 2. A Prova (Validação de Modelos)
Não confiamos no computador de olhos fechados. Nós aplicamos uma "prova" rigorosa chamada **Backtesting**.
*   **Como funciona:** Nós escondemos os dados de 2024 do computador e pedimos para ele "adivinhar" o que aconteceu.
*   Depois, comparamos o palpite dele com a realidade.
*   Se ele errar pouco, ele passa de ano. Se errar muito, nós ajustamos a fórmula.

### 3. A Formatura (Deploy)
Quando encontramos o melhor "aluno" (o modelo que mais acertou), nós o "contratamos".
Ele recebe um carimbo de **"Versão Oficial"** (Champion) e é colocado em um servidor seguro, pronto para trabalhar.

### 4. O Oráculo (Inferência Recorrente)
Toda segunda-feira (ou no início do mês), este modelo oficial acorda, olha para as vendas mais recentes, e gera uma **nova previsão para os próximos 35 dias**.

---

## 🤖 Conheça os Nossos "Robôs" (Arquivos do Projeto)

Na pasta do projeto, você verá vários arquivos com nomes técnicos. Aqui está a tradução do que cada um faz:

| Arquivo Técnico (`.ipynb`) | Apelido | O Que Ele Faz? |
| :--- | :--- | :--- |
| **`cvc_ingestao...`** | **O Entregador** | Busca os dados brutos no banco de dados e os organiza nas prateleiras digitais. |
| **`cvc_consolidacao...`** | **O Bibliotecário** | Organiza as tabelas de apoio (Feriados, Calendário) para que o modelo entenda o contexto das datas. |
| **`cvc_validacao...`** | **O Vestibular** | Testa VÁRIOS tipos de inteligência artificial diferentes e escolhe o venceador. |
| **`cvc_treino_validacao...`** | **O Guardião** | Uma barreira de segurança. Antes de atualizar o sistema, ele verifica se a nova versão é realmente boa. Se não for, ele bloqueia. |
| **`cvc_treino_final...`** | **A Formatura** | Treina o modelo definitivo com TODOS os dados disponíveis até hoje. |
| **`cvc_inferencia...`** | **O Oráculo** | É quem realmente gera os números futuros. Ele consulta o modelo formado e escreve a previsão no banco de dados. |

---

## 📚 Glossário Rápido

Termos que você pode ouvir a equipe de dados falando:

*   **Feature Store:** É como um "supermercado de dados". Em vez de calcular tudo do zero toda vez, guardamos as informações prontas (limpas e organizadas) aqui.
*   **Pipeline:** É a linha de montagem. O dado entra sujo de um lado e sai como uma previsão de venda do outro.
*   **RMSE (Erro Quadrático Médio):** É a nota da prova. Quanto MENOR este número, mais o robô acertou a previsão.
*   **Deploy:** O ato de colocar o sistema no ar para uso real.
*   **Lag:** Olhar para trás. Um "Lag de 7 dias" significa que o modelo está olhando para as vendas de uma semana atrás para decidir a de hoje.

---

## ⚙️ Área Técnica (Para Desenvolvedores)

Abaixo, detalhes técnicos da implementação para a equipe de Engenharia e Ciência de Dados manterem o projeto.

### Estrutura de Pastas
```text
databricks/
├── src/                            # Lógica Python Pura (Modularizada)
│   ├── ingestion/                  # Conectores e Feature Store
│   ├── validation/                 # Configurações e Pipelines de Treino
│   └── deploy/                     # Wrapper MLflow para Produção
│
├── *.ipynb                         # Notebooks de Execução (Databricks Jobs)
```

### Comandos Chave
*   **Modelo Utilizado:** LightGBM (Gradient Boosting) com suporte a variáveis exógenas.
*   **Biblioteca Principal:** Darts (Time Series).
*   **Tracking:** MLflow (com registro no Unity Catalog).