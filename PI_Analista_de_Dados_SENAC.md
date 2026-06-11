# Projeto Integrador — Qualificação Profissional em Análise de Dados
**Instituição:** Senac  
**Curso:** Qualificação Profissional — Analista de Dados  
**Nível:** Iniciante a Intermediário   
**Entrega Final:** Relatório em PDF + Dashboard Power BI + Notebook Python (.ipynb)

---

## 1. Apresentação

Este Projeto Integrador (PI) tem como objetivo consolidar os conhecimentos adquiridos ao longo do curso, integrando as ferramentas e técnicas estudadas: **Python**, **Pandas**, **NumPy** e **Power BI**. Os alunos irão simular o papel de um Analista de Dados em uma empresa do varejo, percorrendo todas as etapas de um projeto real: coleta, limpeza, análise exploratória e visualização de dados.

O trabalho poderá ser realizado individualmente ou em duplas, a critério do docente.

---

## 2. Tema

### 📦 Análise de Desempenho de Vendas — Empresa Fictícia "Varejo Fácil Ltda."

A empresa **Varejo Fácil Ltda.** é uma rede de lojas que vende produtos de diferentes categorias (Eletrônicos, Vestuário, Alimentos e Casa & Decoração). O setor gerencial solicitou à equipe de dados um relatório completo sobre o desempenho de vendas do último ano, com o objetivo de apoiar decisões estratégicas.

Os alunos receberão uma base de dados fictícia (fornecida pelo docente) e deverão responder às perguntas de negócio definidas neste documento.

---

## 3. Dataset

O docente disponibilizará o arquivo `vendas_varejo_fácil.csv` com as seguintes colunas:

| Coluna | Tipo | Descrição |
|---|---|---|
| `id_venda` | int | Identificador único da venda |
| `data_venda` | date | Data da transação |
| `id_cliente` | int | Identificador do cliente |
| `nome_cliente` | str | Nome do cliente |
| `cidade` | str | Cidade onde ocorreu a venda |
| `estado` | str | Estado (UF) |
| `categoria` | str | Categoria do produto |
| `produto` | str | Nome do produto |
| `quantidade` | int | Quantidade de itens vendidos |
| `valor_unitario` | float | Preço unitário do produto |
| `desconto` | float | Percentual de desconto aplicado (0 a 1) |
| `valor_total` | float | Valor total da venda (com desconto) |
| `forma_pagamento` | str | Forma de pagamento (Cartão, PIX, Boleto, Dinheiro) |
| `avaliacao_cliente` | int | Nota de satisfação (1 a 5) |

---

## 4. Perguntas de Negócio

Os alunos deverão responder às seguintes perguntas utilizando Python e/ou Power BI:

**Análise Geral**
1. Qual foi o faturamento total no período analisado?
2. Qual foi o ticket médio por venda?
3. Quantas vendas foram realizadas no total?

**Análise Temporal**

4. Como o faturamento evoluiu mês a mês? Houve sazonalidade?
5. Qual foi o mês com maior e menor volume de vendas?

**Análise por Categoria e Produto**

6. Qual categoria gerou maior receita?
7. Quais são os 5 produtos mais vendidos em quantidade?
8. Qual categoria tem a maior média de avaliação dos clientes?

**Análise Geográfica**

9. Quais são os 5 estados com maior faturamento?
10. Existe relação entre a cidade/estado e a forma de pagamento preferida?

**Análise de Clientes**

11. Qual a distribuição das formas de pagamento utilizadas?
12. Qual a média de avaliação geral dos clientes? Como ela varia por categoria?

---

## 5. Etapas do Projeto

### Etapa 1 — Coleta e Importação dos Dados (Python / Pandas)
**Objetivo:** Carregar o dataset e realizar uma inspeção inicial.

Tarefas:
- Importar o arquivo `.csv` utilizando `pandas`
- Verificar o shape do DataFrame (linhas e colunas)
- Visualizar as primeiras e últimas linhas (`head()`, `tail()`)
- Verificar os tipos de dados (`dtypes`)
- Conferir se há valores nulos (`isnull().sum()`)

Entregável: Notebook com as células executadas e comentadas.

---

### Etapa 2 — Limpeza e Tratamento dos Dados (Python / Pandas)
**Objetivo:** Garantir a qualidade dos dados antes da análise.

Tarefas:
- Tratar valores nulos (substituir ou remover conforme o contexto)
- Converter a coluna `data_venda` para o tipo `datetime`
- Extrair novas colunas: `mes`, `ano`, `trimestre` a partir de `data_venda`
- Verificar e remover duplicatas, se existirem
- Padronizar textos (ex: remover espaços, corrigir capitalização com `.str.strip()` e `.str.title()`)
- Validar se `valor_total` está coerente com `quantidade * valor_unitario * (1 - desconto)`

Entregável: Notebook com o DataFrame limpo e comentários explicando cada decisão.

---

### Etapa 3 — Análise Exploratória de Dados — EDA (Python / Pandas / NumPy)
**Objetivo:** Responder às perguntas de negócio usando código Python.

Tarefas:
- Calcular estatísticas descritivas com `describe()`
- Usar `groupby()` para agregar dados por categoria, estado, mês, etc.
- Usar `value_counts()` para análises de frequência
- Calcular métricas com NumPy (ex: média, mediana, desvio padrão da avaliação)
- Criar pelo menos **3 gráficos** com `matplotlib` ou `seaborn`: (Estes gráficos poderão ser substituídos pelo Dashboard)
  - Gráfico de barras: faturamento por categoria
  - Gráfico de linha: evolução mensal do faturamento
  - Gráfico de pizza ou barras horizontais: distribuição por forma de pagamento

Entregável: Notebook com análises respondendo às 12 perguntas de negócio.

---

### Etapa 4 — Dashboard no Power BI
**Objetivo:** Criar uma visualização interativa para apresentação ao time de gestão.

Tarefas:
- Importar o CSV tratado (ou o original) no Power BI
- Criar as transformações necessárias no Power Query (mesmas da Etapa 2)
- Criar as seguintes medidas DAX:
  - `Faturamento Total = SUM([valor_total])`
  - `Ticket Médio = DIVIDE([Faturamento Total], COUNTROWS(vendas))`
  - `Total de Vendas = COUNTROWS(vendas)`
  - `Avaliação Média = AVERAGE([avaliacao_cliente])`
- Montar um dashboard com **pelo menos 5 visuais**:
  - Cartões com KPIs (Faturamento Total, Ticket Médio, Total de Vendas)
  - Gráfico de barras: Faturamento por Categoria
  - Gráfico de linha: Faturamento por Mês
  - Mapa ou gráfico de barras: Faturamento por Estado
  - Segmentações (filtros) por: Período, Categoria e Estado
- O dashboard deve ter identidade visual (cores consistentes, título, logo fictícia)

Entregável: Arquivo `.pbix` do Power BI.

---

### Etapa 5 — Relatório Final e Apresentação
**Objetivo:** Comunicar os resultados de forma clara e profissional.

Tarefas:
- Elaborar um relatório em PDF (máximo 5 páginas) contendo:
  - Introdução e contexto do problema
  - Metodologia utilizada
  - Principais insights encontrados (com capturas de tela dos gráficos)
  - Conclusões e recomendações para a empresa
- Preparar uma apresentação oral de **10 a 15 minutos** para a turma

Entregável: Relatório em PDF + apresentação oral.

---

## 6. Critérios de Avaliação

| Critério | Peso | Descrição |
|---|---|---|
| Limpeza e qualidade do código Python | 20% | Código organizado, comentado e funcional |
| Profundidade da análise exploratória | 25% | Respostas às perguntas de negócio com embasamento |
| Qualidade do Dashboard Power BI | 25% | Visual claro, correto e com KPIs e filtros funcionando |
| Relatório escrito | 15% | Clareza, coerência e apresentação dos insights |
| Apresentação oral | 15% | Comunicação, domínio do conteúdo e postura profissional |
| **Total** | **100%** | |

**Escala de notas:** 0 a 10, aprovação com nota mínima de 6,0.

---

## 7. Entregáveis — Resumo

Ao final do projeto, cada aluno ou dupla deve entregar:

- [ ] `notebook_analise.ipynb` — Notebook Python com todas as etapas (1 a 3)
- [ ] `dashboard_varejo.pbix` — Arquivo do Power BI com o dashboard completo
- [ ] `relatorio_final.pdf` — Relatório escrito (máx. 5 páginas)
- [ ] Apresentação oral (10–15 min) com perguntas do docente

Todos os arquivos devem ser compactados em um `.zip` com o nome: `PI_NomeAluno_AnalistaDados.zip`  
Link para entrega: (https://classroom.google.com/c/Nzk3NDM3NTk1OTA2/a/Nzk4MTY0NzE3NTQw/details)

---

## 8. Dicas e Orientações ao Aluno

- **Não copie e cole código sem entender** — o docente poderá perguntar sobre qualquer linha durante a apresentação.
- **Comente seu código** com `#` explicando o que cada bloco faz.
- **Pesquise na documentação oficial:** `pandas.pydata.org`, `numpy.org`, e a documentação do Power BI da Microsoft.
- **Salve versões do seu trabalho** para não perder progresso.
- **Em caso de dúvida**, consulte o docente ou pesquise na web — isso faz parte do trabalho real de um analista de dados.
- O dashboard deve ser pensado para **uma pessoa que não é técnica** — clareza é mais importante do que complexidade.

---

## 9. Recursos de Apoio

| Recurso | Link |
|---|---|
| Documentação Pandas | https://pandas.pydata.org/docs/ |
| Documentação NumPy | https://numpy.org/doc/ |
| Documentação Power BI (DAX) | https://learn.microsoft.com/pt-br/power-bi/ |
| Matplotlib | https://matplotlib.org/stable/tutorials/index.html |
| Seaborn | https://seaborn.pydata.org/tutorial.html |
| Python para Análise de Dados (Wes McKinney) | Disponível na biblioteca do Senac |

---

## Anexo A — Script de Geração do Dataset

O docente pode usar o script abaixo para gerar o arquivo `vendas_varejo_fácil.csv`:

```python
import pandas as pd
import numpy as np
from datetime import date, timedelta
import random

np.random.seed(42)
random.seed(42)

n = 2000  # número de registros

categorias = {
    "Eletrônicos": ["Smartphone", "Notebook", "Fone de Ouvido", "Tablet", "Smartwatch"],
    "Vestuário": ["Camiseta", "Calça Jeans", "Tênis", "Vestido", "Jaqueta"],
    "Alimentos": ["Café Premium", "Whey Protein", "Azeite Importado", "Chocolate Belga", "Granola"],
    "Casa & Decoração": ["Luminária", "Tapete", "Quadro Decorativo", "Vaso", "Almofada"]
}

precos = {
    "Smartphone": 1800, "Notebook": 3500, "Fone de Ouvido": 350, "Tablet": 1200, "Smartwatch": 800,
    "Camiseta": 59, "Calça Jeans": 149, "Tênis": 299, "Vestido": 189, "Jaqueta": 249,
    "Café Premium": 45, "Whey Protein": 189, "Azeite Importado": 79, "Chocolate Belga": 35, "Granola": 28,
    "Luminária": 129, "Tapete": 299, "Quadro Decorativo": 189, "Vaso": 89, "Almofada": 69
}

estados = ["SP", "RJ", "MG", "BA", "RS", "PR", "CE", "PE", "GO", "SC"]
cidades_por_estado = {
    "SP": ["São Paulo", "Campinas", "Santos"], "RJ": ["Rio de Janeiro", "Niterói", "Petrópolis"],
    "MG": ["Belo Horizonte", "Uberlândia", "Juiz de Fora"], "BA": ["Salvador", "Feira de Santana", "Vitória da Conquista"],
    "RS": ["Porto Alegre", "Caxias do Sul", "Pelotas"], "PR": ["Curitiba", "Londrina", "Maringá"],
    "CE": ["Fortaleza", "Juazeiro do Norte", "Caucaia"], "PE": ["Recife", "Caruaru", "Olinda"],
    "GO": ["Goiânia", "Anápolis", "Aparecida de Goiânia"], "SC": ["Florianópolis", "Joinville", "Blumenau"]
}

nomes = [f"Cliente_{i:04d}" for i in range(1, 501)]
formas_pagamento = ["Cartão de Crédito", "PIX", "Boleto", "Dinheiro"]

data_inicio = date(2024, 1, 1)
registros = []

for i in range(1, n + 1):
    cat = random.choice(list(categorias.keys()))
    prod = random.choice(categorias[cat])
    estado = random.choice(estados)
    cidade = random.choice(cidades_por_estado[estado])
    qtd = random.randint(1, 5)
    valor_unit = precos[prod] * np.random.uniform(0.9, 1.1)
    desconto = round(random.choice([0, 0, 0, 0.05, 0.10, 0.15, 0.20]), 2)
    valor_total = round(qtd * valor_unit * (1 - desconto), 2)
    dias = random.randint(0, 364)
    data_venda = data_inicio + timedelta(days=dias)
    id_cliente = random.randint(1, 500)
    nome = f"Cliente_{id_cliente:04d}"
    avaliacao = random.choices([1, 2, 3, 4, 5], weights=[2, 5, 15, 40, 38])[0]
    pagamento = random.choices(formas_pagamento, weights=[45, 30, 15, 10])[0]

    registros.append({
        "id_venda": i,
        "data_venda": data_venda,
        "id_cliente": id_cliente,
        "nome_cliente": nome,
        "cidade": cidade,
        "estado": estado,
        "categoria": cat,
        "produto": prod,
        "quantidade": qtd,
        "valor_unitario": round(valor_unit, 2),
        "desconto": desconto,
        "valor_total": valor_total,
        "forma_pagamento": pagamento,
        "avaliacao_cliente": avaliacao
    })

# Inserir alguns valores nulos propositalmente para o exercício de limpeza
df = pd.DataFrame(registros)
indices_nulos = np.random.choice(df.index, size=40, replace=False)
df.loc[indices_nulos[:20], "avaliacao_cliente"] = np.nan
df.loc[indices_nulos[20:], "desconto"] = np.nan

df.to_csv("vendas_varejo_facil.csv", index=False, encoding="utf-8-sig")
print(f"Dataset gerado com {len(df)} registros.")
print(df.head())
```

---

## Anexo B — Estrutura Mínima do Notebook Python

```python
# ============================================================
# PI — Análise de Desempenho de Vendas | Varejo Fácil Ltda.
# Aluno(a): [Nome completo]
# Data: [Data de entrega]
# ============================================================

# --- ETAPA 1: Importação e Inspeção ---
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("vendas_varejo_facil.csv", encoding="utf-8-sig")

print("Shape:", df.shape)
print(df.head())
print(df.dtypes)
print(df.isnull().sum())

# --- ETAPA 2: Limpeza e Tratamento ---
df["data_venda"] = pd.to_datetime(df["data_venda"])
df["mes"] = df["data_venda"].dt.month
df["ano"] = df["data_venda"].dt.year
df["trimestre"] = df["data_venda"].dt.quarter

# ... (continuar com os demais procedimentos)

# --- ETAPA 3: Análise Exploratória ---

# Pergunta 1: Faturamento Total
faturamento_total = df["valor_total"].sum()
print(f"Faturamento Total: R$ {faturamento_total:,.2f}")

# Pergunta 2: Ticket Médio
ticket_medio = df["valor_total"].mean()
print(f"Ticket Médio: R$ {ticket_medio:,.2f}")

# Pergunta 3: Total de Vendas
total_vendas = len(df)
print(f"Total de Vendas: {total_vendas}")

# ... (continuar com as demais perguntas)

# --- GRÁFICO 1: Faturamento por Categoria ---
fat_categoria = df.groupby("categoria")["valor_total"].sum().sort_values(ascending=False)

plt.figure(figsize=(10, 5))
fat_categoria.plot(kind="bar", color="steelblue")
plt.title("Faturamento por Categoria")
plt.xlabel("Categoria")
plt.ylabel("Faturamento (R$)")
plt.xticks(rotation=45)
plt.tight_layout()
plt.savefig("grafico_categoria.png")
plt.show()

# ... (continuar com os demais gráficos e análises)
```

---

*Documento elaborado pelo docente para uso exclusivo na turma de Qualificação Profissional em Análise de Dados — Senac.*  
*Versão 1.0 — Junho/2026*  
*Material gerado com apoio de IA*
