# CrisprGpt

<div align="center">

**CRISPR-GPT: Agentic Automation for Gene-Editing Experiments**  

[![Paper](https://img.shields.io/badge/Paper-Nature%20BME-red?style=for-the-badge)](https://www.nature.com/articles/s41551-025-01463-z) [![Website](https://img.shields.io/badge/Website-genomics.stanford.edu-blue?style=for-the-badge)](https://genomics.stanford.edu) [![Sign Up](https://img.shields.io/badge/Early%20Access-Sign%20Up-green?style=for-the-badge)](https://www.surveymonkey.com/r/G9GCMJV)

🧬 Multi-Agent System for Automated CRISPR Experiment Design and Analysis 🔬

</div>

## Overview

<p align="center">
  <img width="600" alt="CrisprGpt Overview" src="assets/fig1.png">
</p>

CrisprGpt is an innovative Large Language Model (LLM) agent designed to automate and streamline the process of designing gene-editing experiments. By leveraging the power of advanced language models, CrisprGpt assists researchers in planning, executing, and analyzing CRISPR-based gene editing tasks with unprecedented efficiency and accuracy.

CrisprGpt supports four primary gene-editing modalities: **knockout**, **base-editing**, **prime-editing**, and **epigenetic editing**. The system automates 22 individual tasks including CRISPR/Cas system selection, sgRNA design, off-target prediction, delivery method optimization, and experimental validation protocols. Users can interact with CrisprGpt through three distinct modes: (1) **Meta mode** for step-by-step guidance on pre-defined gene-editing workflows, (2) **Auto mode** for customized guidance on free-style user requests, and (3) **QA mode** for real-time answers to ad hoc questions. These modes accommodate different user expertise levels and experimental requirements, from novice researchers seeking structured guidance to experienced scientists needing flexible, custom workflows or quick troubleshooting support.

**Related Work**: This project builds upon our [Genome-Bench](https://github.com/mingyin0312/RL4GenomeBench) research, which developed RL fine-tuning methods to inject expert knowledge from 10+ years of genomics discussions into language models.

## Architecture

<p align="center">
  <img width="830" alt="CrisprGpt Architecture" src="assets/fig2.png">
</p>

The backbone of CrisprGpt involves multi-agent collaboration between four core components:

1. **LLM Planner Agent**: Configures tasks and performs automatic task decomposition and planning based on user requests
2. **Task Executor Agent**: Implements the chain of state machines from the Planner Agent and manages workflow execution
3. **LLM User-Proxy Agent**: Interfaces with the Task Executor on behalf of users, enabling monitoring and corrections
4. **Tool Providers**: Support diverse external tools and connect to search engines or databases via API calls

## Getting Started

### Release Information

Due to safety concerns regarding AI applications in biological research, the complete CrisprGpt codebase (including full data, custom model weights, and proprietary tool integrations) is not publicly available. However, a reference implementation and example workflows are provided to demonstrate the system's architecture and capabilities.

### Prerequisites

- Python 3.9+
- pip or conda package manager

### Installation

bash
# Clone the repository
git clone https://github.com/your-org/crispr-gpt-pub.git
cd crispr-gpt-pub

# Create and activate a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt


### Configuration

Create a `.env` file in the project root with your API keys:

env
OPENAI_API_KEY=your_openai_api_key
# Add other required API keys here


### Quickstart (Reference Implementation)

Run the reference planner to see the multi-agent workflow in action:

bash
python run_planner.py --query "Design a knockout experiment for gene TP53 in HEK293 cells"


### Usage Examples

#### Meta Mode (Guided Workflow)
python
from crispr_gpt import CrisprGpt

agent = CrisprGpt(mode="meta")
result = agent.run_workflow(
    target_gene="BRCA1",
    edit_type="knockout",
    cell_line="MCF7"
)


#### Auto Mode (Custom Requests)
python
agent = CrisprGpt(mode="auto")
response = agent.query(
    "Suggest three sgRNAs for KRAS with minimal off-targets in pancreatic cells"
)


#### QA Mode (Interactive)
python
agent = CrisprGpt(mode="qa")
while True:
    question = input("Ask CRISPR-GPT: ")
    print(agent.answer(question))


## Documentation

For comprehensive documentation, visit our [official website](https://genomics.stanford.edu).

## Citation

If you use CrisprGpt in your research, please cite:

bibtex
@article{crisprgpt2025,
  title={CRISPR-GPT: An LLM Agent for Automated CRISPR Experiment Design},
  author={...},
  journal={Nature Biomedical Engineering},
  year={2025},
  doi={...}
}


## License

This project is licensed under the terms specified in the LICENSE file. Please review the usage restrictions before deployment.

## Disclaimer

CrisprGpt is a research tool intended for academic and educational purposes. It requires human oversight and validation for any experimental applications. Always follow institutional biosafety guidelines and regulatory requirements when conducting gene-editing experiments.
