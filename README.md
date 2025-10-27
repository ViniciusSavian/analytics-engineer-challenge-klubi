# Projeto: Análise de Hábitos e Desempenho Estudantil

Este repositório contém a solução do teste prático para a vaga de Analytics Engineer. O objetivo do projeto é explorar, transformar e analisar um conjunto de dados sobre hábitos de estudantes para identificar fatores que influenciam o desempenho escolar.

Nota: A análise foi originalmente desenvolvida no Google Colab, garantindo reprodutibilidade tanto no ambiente Colab quanto localmente via VS Code/Jupyter.

Sumário
-------
- Visão geral do projeto
- Estrutura do repositório
- Arquitetura Medallion
- Como reproduzir (instalação e execução)
- Principais análises realizadas
- Notas e recomendações

Dataset
-------
O dataset principal está em CSV: `habitos_e_desempenho_estudantil.csv`. Contém variáveis sobre horas de estudo, tempo em redes sociais, saúde mental, frequência de exercícios, dieta e notas de avaliação.

Arquivos importantes
--------------------
- `analise_habitos_desempenho_estudantes.ipynb` — Notebook principal com toda a exploração, engenharia de features, análises estatísticas e visualizações.
- `habitos_e_desempenho_estudantil.csv` — Base de dados usada nas análises.
- `Instrucoes/README.md` — Enunciado e instruções do teste.

Objetivos do projeto
--------------------
1. Explorar e entender a base de dados (tipos, distribuição, valores ausentes).
2. Realizar engenharia de dados: tratamento de dados ausentes, criação de variáveis derivadas e categorização.
3. Executar análise estatística (matriz de correlação, testes de significância) para identificar fatores que influenciam as notas.
4. Gerar visualizações relevantes (mapa de calor de correlação, análise detalhada de variáveis de maior impacto, comparação por faixas).
5. Sintetizar insights acionáveis e recomendações.

Arquitetura Medallion
--------------------
O projeto foi estruturado para salvar informações seguindo a arquitetura Medallion, que organiza os dados em três camadas principais:

### Bronze (Raw)
- Dados brutos importados do CSV
- Preservação do formato original
- Documentação de fonte e timestamp
- Validação inicial de schema

### Silver (Refined)
- Dados limpos e padronizados
- Tratamento de valores ausentes
- Correção de tipos de dados
- Remoção de inconsistências
- Criação de variáveis derivadas básicas

### Gold (Curated)
- Dados agregados e transformados
- Features engineered (ex: score de hábitos saudáveis)
- Métricas calculadas
- Dados prontos para análise
- Views específicas para diferentes análises

Esta arquitetura garantiu:
- Rastreabilidade das transformações
- Reprodutibilidade das análises
- Qualidade progressiva dos dados
- Separação clara entre dados brutos e transformados
- Facilidade de manutenção e evolução

Como executar
-------------

### Opção 1: Google Colab (Recomendado)
1. Acesse o Google Colab (https://colab.research.google.com)
2. Faça o upload do notebook `analise_habitos_desempenho_estudantes.ipynb`
3. Faça o upload do arquivo `habitos_e_desempenho_estudantil.csv` para o ambiente Colab
4. Execute as células em ordem

### Opção 2: Local (VS Code / Jupyter)

1. Crie e ative um ambiente virtual (Windows/PowerShell):

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

2. Instale as dependências do arquivo requirements.txt:

```powershell
pip install --upgrade pip
pip install -r requirements.txt
```

3. Escolha uma das opções:

#### VS Code
- Abra a pasta do repositório
- Instale a extensão "Jupyter" se necessário
- Abra `analise_habitos_desempenho_estudantes.ipynb`
- Selecione o kernel Python (.venv)

#### Jupyter Lab/Notebook
```powershell
jupyter lab
# ou
jupyter notebook
```

4. Execute as células em ordem

Notas sobre ambiente e kernel
----------------------------
- Certifique-se de selecionar o kernel Python correto no VS Code (ou o ambiente virtual ativado no terminal) antes de instalar pacotes ou executar o notebook.
- Se o notebook reportar falta de pacotes, instale-os com `pip install <pacote>` no ambiente ativo.

Principais Descobertas e Insights
-----------------------------

### Análise de Dados e Qualidade
- Base com 1.000 registros e 16 variáveis originais
- Tratamento específico para dados ausentes em educação parental (9.1%)
- Alta qualidade geral dos dados (sem duplicatas, poucos missing values)
- Criação de 8 variáveis derivadas estratégicas

### Correlações e Fatores de Impacto
- Horas de estudo: correlação positiva forte (r > 0.60, p < 0.001)
- Frequência de exercícios: impacto positivo moderado
- Tempo em redes sociais: correlação negativa significativa
- Qualidade do sono: fator importante para desempenho

### Insights Principais
1. Estudantes com rotina equilibrada (estudo + exercício) têm melhor desempenho
2. Tempo excessivo em tela (>4h/dia) está associado a notas mais baixas
3. Padrão de sono regular contribui positivamente para as notas
4. Suporte familiar (nível educacional dos pais) tem correlação positiva
5. Saúde mental tem impacto significativo no desempenho

### Visualizações Chave
- Mapa de calor de correlações entre todas variáveis
- Análise detalhada do impacto das horas de estudo
- Comparações por grupos socioeconômicos
- Dashboard integrado com métricas principais

Recomendações Práticas
------------------------------

### Para Estudantes
1. Estabelecer rotina de estudos consistente (4-6h/dia ideal)
2. Limitar tempo em redes sociais e streaming (<4h/dia)
3. Manter sono regular (7-8h/noite recomendado)
4. Praticar exercícios regularmente
5. Buscar equilíbrio entre atividades acadêmicas e bem-estar

### Para Educadores
1. Monitorar sinais de saúde mental dos alunos
2. Implementar programas de gestão de tempo
3. Criar ambiente que incentive hábitos saudáveis
4. Oferecer suporte adicional para grupos específicos

### Próximos Passos (Técnicos)
- Criar pipeline automatizada para ingestão e transformação
- Desenvolver dashboard interativo para acompanhamento
- Implementar sistema de alertas para padrões críticos
- Expandir análise com dados longitudinais
- Realizar análises mais granulares por subgrupos
