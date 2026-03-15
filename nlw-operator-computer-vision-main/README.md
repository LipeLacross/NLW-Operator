# 🚀 NLW Operator — Trilha Python: Visão Computacional

Bem-vindo ao repositório do projeto **NLW Operator Visão Computacional**. Este workspace contém uma coleção de projetos e experimentos desenvolvidos durante a trilha Python de Visão Computacional da NLW Operator da Rocketseat, focando em Deep Learning, Reconhecimento de Gestos em tempo real e técnicas avançadas de Visão Computacional.

redes neurais convulucipnas cnns vs vision transformers vit
---
## 📂 Estrutura do Projeto

Este monorepo está dividido em três módulos principais, um para cada aula:

### 1.arquitetura [🧠 LeNet-5 MNIST](./lenet)
Uma implementação moderna da clássica arquitetura **LeNet-5** utilizando **PyTorch** para classificação de dígitos manuscritos.
- **Tecnologias principais**: PyTorch, Jupyter, Matplotlib.
- **Destaques**: Camadas CNN customizadas, visualização de mapas de características (feature maps), análise de erros no dataset MNIST.

### 2. [🔬 Recognition System & Lab](./recog_system)
A "sala de máquinas" onde os modelos de gestos são treinados, junto com notebooks exploratórios para modelos SOTA (State of the Art).
- **Tecnologias principais**: Scikit-Learn, MediaPipe, YOLO, CLIPSeg, Gemini Vision.cloud vision api, api gemini hiugging face
- **Destaques**: Pipeline de coleta de dados customizado, scripts de treinamento de modelo e experimentação com detecgging faceção de objetos e segmentação.
- **⚠️ Requisito**: Necessário baixar modelos do MediaPipe (veja o README do módulo).
https://ai.google.dev/edge/mediapipe/solutions/guide

---
Filter
Overview
About the Preview

Tasks

Model Maker

Studio

Vision tasks
Object detection

Image classification

Image segmentation

Interactive segmentation

Gesture recognition

Hand landmark detection

Image embedding

Face detection

Face landmark detection

Pose landmark detection

Holistic landmark detection

Text tasks
Text classification

Text embedding

Language detection

Audio tasks
Audio classification

### 3. [🖐️ Computer Vision App](./computer_vision_app)
Uma aplicação web de alta performance construída com **FastHTML** e **MediaPipe** para reconhecimento de gestos faciais/mãos em tempo real via WebSockets.
- **Tecnologias principais**: FastHTML, OpenCV, MediaPipe, Scikit-Learn.
- **Destaques**: Processamento de vídeo de baixa latência, interface interativa, monitoramento de FPS em tempo real.
- **⚠️ Requisito**: Necessário baixar modelos do MediaPipe (veja o README do módulo).



## 🛠️ Stack Tecnológica Global

- **Linguagem**: ![Python](https://img.shields.io/badge/Python-3.14+-3776AB?style=flat-square&logo=python&logoColor=white)
- **Gerenciador de Pacotes**: ![uv](https://img.shields.io/badge/uv-Package%20Manager-purple?style=flat-square)
- **Frameworks**: FastHTML, PyTorch, MediaPipe, OpenCV, Scikit-Learn.
- **AI/ML**: YOLO-S, CLIPSeg, Google Gemini API.

---

## 🚀 Como Começar

### Pré-requisitos

Certifique-se de ter o [uv](https://github.com/astral-sh/uv) instalado. Ele é utilizado em todos os módulos para um gerenciamento de dependências rápido e confiável.

### Instalação

1. **Clone o repositório**:
   ```bash
   git clone <repository-url>
   cd nlw-2026-computer-vision
   ```

2. **Explore os Módulos**:
   Cada subpasta possui seu próprio `pyproject.toml` e ambiente. Navegue até um módulo específico para começar:
   ```bash
   cd computer_vision_app
   uv sync
   ```foi usado o https://excalidraw.com/ para fazer explica~çoes visuai
https://huggingface.co/models e vai em tasks
teve classificaçção, localização e segmentação
---
f
## 📄 Licença

Este projeto foi desenvolvido para fins educacionais durante o **NLW Operator** da Rocketseat.

*Feito com ❤️ por Arthur Kamienski*
