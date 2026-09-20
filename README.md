# teste-agentes-ia-2026
Fechado. Aqui está o README completo pra você colar no agente-ia-treino. Está em bloco de código pra facilitar o copiar/colar no celular.

Onde eu não tinha certeza do conteúdo exato, deixei marcado com <!-- ajuste --> como comentário HTML — não aparece quando renderiza no GitHub, mas fica no arquivo pra você revisar depois. Se estiver tudo certo, só apaga os comentários.

```markdown
# agente-ia-treino

> Projeto de treinamento prático voltado à construção de **agentes de IA** capazes de escrever, executar scripts e gerar escopo automaticamente, integrando bancos de dados relacionais (PostgreSQL/Neon e Oracle) e diferentes ambientes de execução.

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)]()
[![R](https://img.shields.io/badge/R-4.x-276DC3.svg)]()
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-336791.svg)]()
[![Neon](https://img.shields.io/badge/Neon-Serverless%20PG-00E599.svg)]()
[![Oracle](https://img.shields.io/badge/Oracle-21c%20XE-F80000.svg)]()
[![Codespaces](https://img.shields.io/badge/GitHub-Codespaces-181717.svg)]()
[![Status](https://img.shields.io/badge/status-em%20evolu%C3%A7%C3%A3o-yellow.svg)]()

---

## 📌 Sobre o projeto

Este repositório reúne a implementação de **agentes de IA** desenvolvidos durante um treinamento prático. O foco é demonstrar, de ponta a ponta, como um agente pode:

- **Escrever** código e artefatos a partir de instruções em linguagem natural;
- **Executar scripts** de forma controlada em ambientes isolados;
- **Gerar o escopo completo** de uma tarefa (estrutura, dados, execução e saída);
- **Interagir com bancos de dados relacionais** para persistir e consultar resultados.

O projeto foi construído em múltiplos ambientes — **GitHub Codespaces**, **Oracle 21c XE** e **Neon (PostgreSQL serverless)** — justamente para validar que o mesmo agente funciona em contextos diferentes, tanto em nuvem quanto local.

---

## 🧠 O que o agente faz

1. Recebe uma instrução do usuário (texto/comando).
2. Interpreta o objetivo e **gera o escopo** da tarefa.
3. **Escreve** os scripts necessários (Python e/ou R).
4. **Executa** os scripts em ambiente controlado.
5. Persiste e consulta resultados em **PostgreSQL (Neon)** ou **Oracle 21c XE**.
6. Retorna a saída consolidada ao usuário.

<!-- ajuste: se o fluxo real tiver etapas diferentes, edite a lista acima -->

---

## 🧰 Stack utilizada

| Camada | Tecnologia |
|---|---|
| Linguagem principal | Python 3.10+ |
| Análise de dados / scripts estatísticos | R |
| Banco relacional (nuvem) | PostgreSQL via **Neon** (serverless) |
| Banco relacional (local/on-prem) | **Oracle 21c XE** |
| Banco relacional (local) | PostgreSQL |
| Ambiente de desenvolvimento | **GitHub Codespaces** |
| Versionamento | Git + GitHub |

---

## 🏗️ Arquitetura (visão geral)

```
[ Instrução do usuário ]
          │
          ▼
[  Agente de IA  ]  ──►  Gera escopo + escreve scripts
          │
          ├──►  Executa scripts (Python / R)
          │
          ├──►  PostgreSQL (Neon)          ← nuvem / serverless
          ├──►  Oracle 21c XE              ← local
          └──►  PostgreSQL (local)         ← local
          │
          ▼
[ Saída consolidada ao usuário ]
```

<!-- ajuste: substitua pelo diagrama/estrutura real do seu projeto -->

---

## 📁 Estrutura do repositório

```
agente-ia-treino/
├── README.md
├── requirements.txt          # dependências Python
├── .env.example              # modelo de variáveis de ambiente (sem segredos)
├── .gitignore
├── src/
│   ├── agente.py             # lógica principal do agente
│   ├── executor.py           # execução controlada de scripts
│   ├── db_postgres.py        # conexão PostgreSQL / Neon
│   ├── db_oracle.py          # conexão Oracle 21c XE
│   └── config.py             # leitura de variáveis de ambiente
├── r/
│   └── analise.R             # scripts em R
└── docs/
    └── escopo.md             # exemplos de escopo gerados pelo agente
```

<!-- ajuste: reflita aqui exatamente o que existe no repositório -->

---

## 🚀 Como executar

### 1. Clonar o repositório
```bash
git clone https://github.com/alvarohsh-afk/agente-ia-treino.git
cd agente-ia-treino
```

### 2. Criar ambiente virtual (Python)
```bash
python -m venv .venv
source .venv/bin/activate      # Linux/macOS
# .venv\Scripts\activate       # Windows
```

### 3. Instalar dependências
```bash
pip install -r requirements.txt
```

### 4. Configurar variáveis de ambiente
```bash
cp .env.example .env
# edite .env com suas credenciais:
#   DATABASE_URL=postgresql://...   (Neon)
#   ORACLE_DSN=...                  (Oracle 21c XE)
#   OPENAI_API_KEY=...              (se aplicável)
```

> 🔒 **Nunca** faça commit do arquivo `.env`. Ele já está no `.gitignore`.

### 5. Executar o agente
```bash
python -m src.agente
```

<!-- ajuste: comando real de execução, se for diferente -->

---

## 🗄️ Bancos de dados suportados

### Neon (PostgreSQL serverless)
- Ideal para ambientes efêmeros como **Codespaces**.
- Conexão via `DATABASE_URL` (string completa).
- Escala a zero quando não está em uso — bom para economizar franquia gratuita.

### Oracle 21c XE
- Usado para validar o agente contra um banco corporativo.
- Conexão via `ORACLE_DSN` + usuário/senha em variáveis de ambiente.

### PostgreSQL local
- Alternativa offline para desenvolvimento e testes.

<!-- ajuste: adicione aqui qualquer detalhe específico de configuração que você usou -->

---

## 🔐 Segurança

- Credenciais **nunca** são versionadas — apenas `.env.example` com valores fictícios.
- Uso de variáveis de ambiente e secrets do Codespaces.
- Conexões com banco sempre por string em variável de ambiente, nunca hardcoded.
- Se você clonar este projeto, gere suas próprias chaves e bancos.

---

## 🗺️ Roadmap

- [x] Estrutura inicial do projeto
- [x] Integração com PostgreSQL (Neon) e Oracle 21c XE
- [x] Execução de scripts Python e R pelo agente
- [x] Geração de escopo automatizada
- [ ] Testes automatizados (`pytest`)
- [ ] Pipeline de CI (GitHub Actions)
- [ ] Interface de linha de comando dedicada
- [ ] Documentação de exemplos reais em `docs/`

<!-- ajuste: marque/desmarque conforme a realidade -->

---

## 🧪 Testes

```bash
pytest -v
```

<!-- ajuste: se ainda não há testes, deixe a seção mas com aviso, ou remova -->

---

## 👤 Autor

**Alvaro H. S. F.**
- GitHub: [@alvarohsh-afk](https://github.com/alvarohsh-afk)

---

## 📄 Licença

Distribuído sob a licença **MIT**. Veja `LICENSE` para mais detalhes.

<!-- ajuste: se for outra licença, troque aqui -->
```

Como colar no celular (passo a passo)

1. Abra o repositório agente-ia-treino no app do GitHub ou no navegador.
2. Toque em README.md → ícone de lápis ✏️.
3. Apague tudo, cole o conteúdo acima.
4. Role até o fim → Commit changes → mensagem tipo docs: reestrutura README.
5. Confirme.

O que revisar depois (quando tiver notebook)

Procure por <!-- ajuste --> no arquivo. Cada um indica um ponto onde eu não tinha certeza e você decide se mantém, muda ou apaga. São 8 no total, todos comentados — não aparecem na página renderizada.

Se quiser, me diz o que está diferente do que eu escrevi (estrutura de pastas, comando de execução, se tem R de verdade, se o agente usa OpenAI ou não) e eu já te devolvo a versão 2 corrigida.