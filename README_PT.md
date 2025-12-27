# CrisprGpt

<div align="center">

**CRISPR-GPT: Automação Baseada em Agentes para Experimentos de Edição Gênica**  

[![Paper](https://img.shields.io/badge/Paper-Nature%20BME-red?style=for-the-badge)](https://www.nature.com/articles/s41551-025-01463-z) [![Website](https://img.shields.io/badge/Website-genomics.stanford.edu-blue?style=for-the-badge)](https://genomics.stanford.edu) [![Sign Up](https://img.shields.io/badge/Early%20Access-Sign%20Up-green?style=for-the-badge)](https://www.surveymonkey.com/r/G9GCMJV)

🧬 Sistema Multi-Agente para Design e Análise Automatizada de Experimentos CRISPR 🔬

</div>

## Visão Geral

<p align="center">
  <img width="600" alt="Visão Geral CrisprGpt" src="assets/fig1.png">
</p>

O CrisprGpt é um inovador Agente de Linguagem (LLM) projetado para automatizar e agilizar o processo de design de experimentos de edição gênica. Aproveitando o poder de modelos de linguagem avançados, o CrisprGpt auxilia pesquisadores no planejamento, execução e análise de tarefas de edição genética baseadas em CRISPR com eficiência e precisão sem precedentes.

O CrisprGpt suporta quatro modalidades principais de edição gênica: **knockout**, **base-editing**, **prime-editing** e **epigenetic editing**. O sistema automatiza 22 tarefas individuais, incluindo seleção de sistema CRISPR/Cas, design de sgRNA, predição de off-target, otimização de métodos de entrega e protocolos de validação experimental. Os usuários podem interagir com o CrisprGpt através de três modos distintos: (1) **Modo Meta** para orientação passo a passo em fluxos de trabalho predefinidos, (2) **Modo Auto** para orientação personalizada em solicitações de estilo livre e (3) **Modo QA** para respostas em tempo real a perguntas ad hoc. Esses modos acomodam diferentes níveis de expertise dos usuários e requisitos experimentais.

**Trabalho Relacionado**: Este projeto baseia-se em nossa pesquisa [Genome-Bench](https://github.com/mingyin0312/RL4GenomeBench), que desenvolveu métodos de fine-tuning com RL para injetar conhecimento especializado de discussões de genomics dos últimos 10+ anos em modelos de linguagem.

## Arquitetura

<p align="center">
  <img width="830" alt="Arquitetura CrisprGpt" src="assets/fig2.png">
</p>

A estrutura do CrisprGpt envolve colaboração multi-agente entre quatro componentes principais:

1. **Agente Planejador LLM**: Configura tarefas e realiza decomposição automática e planejamento baseado nas solicitações do usuário
2. **Agente Executor de Tarefas**: Implementa a cadeia de máquinas de estado do Agente Planejador e gerencia a execução do fluxo de trabalho
3. **Agente Usuário-Proxy LLM**: Interface com o Executor de Tarefas em nome dos usuários, permitindo monitoramento e correções
4. **Provedores de Ferramentas**: Suportam diversas ferramentas externas e conectam-se a motores de busca ou bancos de dados via chamadas de API

## Começando

### Informações de Release

Devido a preocupações de segurança relacionadas a aplicações de IA em pesquisa biológica, o codebase completo do CrisprGpt (incluindo dados completos, pesos de modelos customizados e integrações de ferramentas proprietárias) não está disponível publicamente. No entanto, uma implementação de referência e fluxos de trabalho de exemplo são fornecidos para demonstrar a arquitetura e capacidades do sistema.

### Pré-requisitos

- Python 3.9+
- Gerenciador de pacotes pip ou conda

### Instalação

bash
# Clonar o repositório
git clone https://github.com/your-org/crispr-gpt-pub.git
cd crispr-gpt-pub

# Criar e ativar ambiente virtual
python -m venv venv
source venv/bin/activate  # No Windows: venv\Scripts\activate

# Instalar dependências
pip install -r requirements.txt


### Configuração

Crie um arquivo `.env` na raiz do projeto com suas chaves de API:

env
OPENAI_API_KEY=sua_chave_openai
# Adicione outras chaves de API necessárias aqui


### Quickstart (Implementação de Referência)

Execute o planejador de referência para ver o fluxo de trabalho multi-agente em ação:

bash
python run_planner.py --query "Design um experimento de knockout para o gene TP53 em células HEK293"


### Exemplos de Uso

#### Modo Meta (Fluxo de Trabalho Guiado)
python
from crispr_gpt import CrisprGpt

agent = CrisprGpt(mode="meta")
result = agent.run_workflow(
    target_gene="BRCA1",
    edit_type="knockout",
    cell_line="MCF7"
)


#### Modo Auto (Solicitações Customizadas)
python
agent = CrisprGpt(mode="auto")
response = agent.query(
    "Sugira três sgRNAs para KRAS com off-targets mínimos em células pancreáticas"
)


#### Modo QA (Interativo)
python
agent = CrisprGpt(mode="qa")
while True:
    question = input("Pergunte ao CRISPR-GPT: ")
    print(agent.answer(question))


## Documentação

Para documentação abrangente, visite nosso [site oficial](https://genomics.stanford.edu).

## Citação

Se você usar o CrisprGpt em sua pesquisa, cite:

bibtex
@article{crisprgpt2025,
  title={CRISPR-GPT: An LLM Agent for Automated CRISPR Experiment Design},
  author={...},
  journal={Nature Biomedical Engineering},
  year={2025},
  doi={...}
}


## Licença

Este projeto é licenciado sob os termos especificados no arquivo LICENSE. Por favor, revise as restrições de uso antes da implantação.

## Isenção de Responsabilidade

O CrisprGpt é uma ferramenta de pesquisa destinada a fins acadêmicos e educacionais. Ele requer supervisão humana e validação para quaisquer aplicações experimentais. Sempre siga as diretrizes de biossegurança institucionais e requisitos regulatórios ao conduzir experimentos de edição genética.
