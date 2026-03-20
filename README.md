# fiap2_fase2_cap1
 Desafio Integrador: IA entre Robôs, Sinapses e Medicina

# FIAP - Faculdade de Informática e Administração Paulista

<p align="center">
<a href= "https://www.fiap.com.br/"><img src="assets/logo-fiap.png" alt="FIAP - Faculdade de Informática e Admnistração Paulista" border="0" width=40% height=40%></a>
</p>

<br>

# CardioIA – Diagnóstico Automatizado – IA no Estetoscópio Digital

## Atividade em Grupo: FIAP - 2026/3 - Fase2 Cap1

## 👨‍🎓 Integrantes: 
- <a href="">Alice C. M. Assis - RM 566233</a>
- <a href="">Leonardo S. Souza - RM 563928</a>
- <a href="">Lucas B. Francelino - RM 561409</a> 
- <a href="">Pedro L. T. Silva - RM 561644</a> 
- <a href="">Vitor A. Bezerra - RM 563001</a>

## 👩‍🏫 Professores:
### Tutor(a)
- <a>Caique Nonato da Silva Bezerra</a>
### Coordenador(a)
- <a href="profandre.chiovato@fiap.com.br">André Godoi Chiovato</a>


# CardioIA — Triagem Inteligente em Cardiologia

> *"O estetoscópio digital do século XXI."*

Doenças cardiovasculares são a principal causa de morte no mundo. O diagnóstico precoce depende de profissionais especializados e exames que nem sempre são acessíveis. Este projeto cria uma ferramenta de triagem inteligente que auxilia na identificação de pacientes em alto risco cardíaco com base em dados clínicos simples — democratizando um primeiro nível de avaliação preventiva.

---

## Contexto Clínico — Manchester Triage System

O **Manchester Triage System (MTS)** é um protocolo de triagem clínica criado em 1994 na Inglaterra e amplamente utilizado em pronto-socorros no Brasil. Ele classifica pacientes em 5 níveis de prioridade por cor:

| Cor | Nível | Tempo máximo de atendimento |
|---|---|---|
| 🔴 Vermelho | Emergência | Imediato |
| 🟠 Laranja | Muito urgente | 10 minutos |
| 🟡 Amarelo | Urgente | 60 minutos |
| 🟢 Verde | Pouco urgente | 120 minutos |
| 🔵 Azul | Não urgente | 240 minutos |

O processo não começa pelo diagnóstico — começa pelo **sintoma principal** relatado pelo paciente. A partir daí, o profissional segue fluxogramas com perguntas que afunilam a gravidade.

### Por que o MTS inspira este projeto?

Em um sistema real de triagem cardíaca, a classificação de gravidade nunca vem só do texto. Ela depende de queixa principal, sinais vitais, nível de consciência e escala de dor. Sem esses dados, um paciente com "dor no peito" pode ser infarto ou ansiedade — o texto sozinho não resolve.

Este projeto **simplifica conscientemente** essa lógica para fins acadêmicos, aplicando classificação binária (alto risco / baixo risco) inspirada no MTS. As classes vermelho e laranja do protocolo original mapeiam para **alto risco**; verde e azul mapeiam para **baixo risco**.

Essa limitação é documentada intencionalmente: reconhecê-la é parte do exercício de desenvolvimento responsável de IA.

---

## Objetivo

Desenvolver um módulo inteligente capaz de analisar relatos clínicos textuais, reconhecer sintomas cardíacos e propor diagnósticos assistidos — demonstrando na prática a diferença entre um **sistema baseado em regras** e um **sistema que aprende com dados**.

---

## Estrutura do Projeto

```

```

---

## Parte 1 — Sistema Baseado em Regras

### Como funciona

O código lê cada frase do arquivo `sintomas.txt` e compara com o mapa de conhecimento (`conhecimento.csv`). Se encontrar correspondência entre os sintomas relatados e os padrões mapeados, sugere um diagnóstico com nível de gravidade e especialidade recomendada.

**Lógica:**
```
Frase do paciente → Extração de palavras-chave → Matching com conhecimento.csv → Diagnóstico sugerido
```

### Limitação intencional

O sistema de regras só reconhece o que foi explicitamente mapeado. Se um paciente descrever "meu peito tá pesado" em vez de "aperto no tórax", o sistema falha — porque depende de vocabulário fixo. Essa fragilidade é demonstrada nas frases 21 a 30 do arquivo `sintomas.txt`, que usam linguagem informal e ambígua propositalmente.

Essa falha é o argumento central que justifica a existência da Parte 2.

### Arquivos

| Arquivo | Descrição |
|---|---|
| `sintomas.txt` | 30 relatos simulados de pacientes cardiológicos |
| `conhecimento.csv` | 40 associações entre sintomas e diagnósticos com gravidade e especialidade |
| `parte1_extracao.py` | Código de extração e sugestão de diagnóstico |

---

## Parte 2 — Classificador com Machine Learning

### Como funciona

Em vez de programar regras manualmente, o modelo **aprende padrões** a partir de exemplos rotulados. O pipeline é:

```
triagem.csv → TF-IDF (vetorização) → Modelo ML → Classificação de risco → Avaliação
```

**TF-IDF** transforma cada frase em um vetor numérico, pesando palavras que são importantes para distinguir alto de baixo risco. O modelo aprende quais combinações de palavras indicam emergência.

### Por que não apenas regras?

| | Sistema de Regras (Parte 1) | Machine Learning (Parte 2) |
|---|---|---|
| Conhecimento | Programado manualmente | Aprendido dos dados |
| Flexibilidade | Baixa — vocabulário fixo | Alta — generaliza variações |
| Transparência | Total | Parcial |
| Necessidade de dados | Não | Sim |
| Falha típica | Não reconhece variações de linguagem | Precisa de volume suficiente de dados |

### Limitações conhecidas do modelo

- Com 80 frases de treino, o modelo tem dados insuficientes para generalizar bem em produção. A acurácia alta no teste pode refletir **overfitting**, não qualidade real.
- A base está levemente desbalanceada (30 alto risco / 50 baixo risco), o que é **intencional e realista** — em triagem cardíaca, a maioria dos casos que chegam é baixo risco. Isso pode fazer o modelo ser mais conservador na classificação de alto risco.
- Sem sinais vitais (pressão arterial, frequência cardíaca, SpO2), a classificação por texto tem limite clínico real. Um sistema de produção precisaria dessas variáveis.

### Arquivos

| Arquivo | Descrição |
|---|---|
| `triagem.csv` | 80 frases rotuladas (alto risco / baixo risco) |
| `parte2_classificador.ipynb` | Notebook com TF-IDF, treinamento, avaliação e análise |

---

## Resultados

> ⚠️ *Seção a ser preenchida após execução do código.*

**Parte 1 — Extração de sintomas:**
- Total de frases analisadas: 30
- Diagnósticos identificados corretamente: `___`
- Frases sem correspondência no mapa: `___`
- Principais falhas observadas: `___`

**Parte 2 — Classificador ML:**
- Modelo utilizado: `___`
- Acurácia no conjunto de teste: `___`
- Matriz de confusão: `___`
- Observações sobre viés ou padrões identificados: `___`

---

## Reflexão — IA Responsável

Este projeto toca em um dos dilemas centrais da IA aplicada à saúde: **um modelo que erra para o lado errado pode custar vidas**.

Classificar um infarto como baixo risco é infinitamente mais grave do que classificar ansiedade como alto risco. Por isso, na análise dos resultados, observamos especialmente os **falsos negativos** — casos de alto risco classificados incorretamente como baixo risco.

Sistemas reais de triagem nunca substituem o julgamento clínico. Eles auxiliam, priorizam e alertam. Este projeto replica essa filosofia em escala acadêmica.

---

## Como Executar

```
```

---

## Demonstração

> 🎥 Link do vídeo no YouTube: `[a ser adicionado]`

