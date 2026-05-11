# TCC

# Segmentação Semântica em Ortomosaicos

Este repositório contém a implementação e os experimentos realizados para a segmentação de copas de Araucárias utilizando Redes Neurais Convolucionais (CNNs). O projeto compara o desempenho das arquiteturas **U-Net**, **SegNet** e **DeepLabv3+** em diferentes cenários de dados.

## 📌 Visão Geral do Projeto

O objetivo deste trabalho é identificar e mapear exemplares de *Araucaria angustifolia* em imagens aéreas de alta resolução capturadas por drones. A metodologia abrange desde o pré-processamento do ortomosaico (*image splitting*) até a validação estatística dos modelos treinados.

### Arquiteturas Avaliadas:
* **U-Net:** Foco em precisão de bordas via *skip connections*.
* **SegNet:** Arquitetura eficiente baseada em índices de *pooling*.
* **DeepLabv3+:** Segmentação multiescala com convoluções atrosas (ASPP).

---

## 🛠️ Tecnologias e Bibliotecas

O projeto foi desenvolvido em **Python 3.13.6** e as seguintes bibliotecas são necessárias:

* **[PyTorch](https://pytorch.org/):** Framework principal para construção e treinamento das redes.
* **[Torchvision](https://pytorch.org/vision/stable/index.html):** Aplicação de *Data Augmentation* e utilitários de visão.
* **[NumPy](https://numpy.org/):** Manipulação de matrizes e tensores.
* **[Scikit-Learn](https://scikit-learn.org/):** Divisão dos conjuntos de treino/validação/teste.
* **[Matplotlib](https://matplotlib.org/):** Geração de gráficos e visualização de máscaras.
* **[SciPy](https://scipy.org/):** Execução do Teste Estatístico de Wilcoxon.
* **[Pillow (PIL)](https://python-pillow.org/):** Processamento básico de imagens.

---

## 🚀 Como Executar o Código

### 1. Requisitos de Hardware e Ambiente
Recomenda-se fortemente o uso de uma **GPU NVIDIA** para acelerar o treinamento, devido ao alto custo computacional das redes convolucionais (especialmente *U-Net* e *DeepLabv3+*). 
* **Local:** Certifique-se de instalar a versão do PyTorch compatível com a sua versão do CUDA Toolkit.
* **Nuvem:** Caso utilize o *Google Colab* ou plataformas similares, lembre-se de alterar o ambiente de execução para "GPU" antes de rodar os scripts.

### 2. Organização do Conjunto de Dados
Antes de executar os códigos, é necessário consolidar as imagens na estrutura de pastas correta. Na mesma raiz onde estão os arquivos de código, crie a seguinte hierarquia:

```text
📁 raiz_do_projeto/
├── 📁 tiles/
│   ├── 📁 image/  <-- (Junte aqui todas as imagens extraídas de "image_part1" e "image_part2")
│   └── 📁 mask/   <-- (Adicione aqui todas as máscaras correspondentes)
├── 📓 Unet_Original_Filtrado.ipynb
└── ...
```
Nota explicativa: Como o volume original de imagens é alto, os arquivos foram divididos em duas partes (image_part1 e image_part2). Você deve extrair o conteúdo de ambas e mesclar tudo dentro da pasta tiles/image/.

### 3. Configuração e Execução dos Testes
Os experimentos foram estruturados em formato de Jupyter Notebook. Para executar os treinamentos, abra o notebook da rede desejada e navegue até o último bloco de código.

Lá estão presentes as variáveis globais que controlam a execução. Você pode ajustá-las conforme a necessidade do seu teste:

- seeds: Define as sementes aleatórias de inicialização (ex: 16, 32, 64, 128) para garantir a reprodutibilidade.

- num_rodadas: Quantidade de execuções independentes que serão feitas para cada seed.

- cenario: Define qual abordagem de dados será utilizada (Original, Filtrado ou Augmentation).

- arquivo_saida: Define o nome do arquivo de log (.csv) onde as métricas (Tempo, IoU, F1-Score, Épocas) serão salvas.

Após configurar estes parâmetros, basta executar todas as células do notebook sequencialmente.
