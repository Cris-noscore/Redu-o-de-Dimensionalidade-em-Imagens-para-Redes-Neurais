# Conversão de Imagens para Níveis de Cinza e Binarização

Este projeto é um script Python desenvolvido para o Google Colab que realiza a conversão de imagens coloridas em níveis de cinza e, em seguida, binariza essas imagens (transformação para preto e branco). O objetivo é demonstrar técnicas básicas de processamento de imagem utilizando Python sem o uso de bibliotecas que realizem essas operações automaticamente.

## Funcionalidades

- **Upload de Imagem**: Permite ao usuário carregar uma imagem do seu computador.
- **Conversão para Níveis de Cinza**: Converte a imagem colorida em uma representação em tons de cinza utilizando uma fórmula ponderada.
- **Binarização**: Aplica um limiar (threshold) na imagem em escala de cinza para transformá-la em uma versão binarizada (preto e branco).
- **Visualização**: Exibe a imagem original, a imagem em níveis de cinza e a imagem binarizada em uma única visualização para comparação.

## Como Usar

1. **Clone o Repositório**:
   ```bash```
   git clone https://github.com/Cris-noscore/Redu-o-de-Dimensionalidade-em-Imagens-para-Redes-Neurais.git
   cd Redu-o-de-Dimensionalidade-em-Imagens-para-Redes-Neurais 

   Abra o Google Colab:

Acesse Google Colab e crie um novo notebook.
Copie o Código:

Copie o código do script incluído no arquivo principal (por exemplo, script.py) para uma célula no Google Colab.
Execute o Código:

Execute a célula e faça o upload de uma imagem no formato desejado.
O script processará a imagem e exibirá os resultados.
Código
O código principal para a transformação de imagens está contido no arquivo script.py. Você pode visualizar o código aqui:

# Importando bibliotecas necessárias
import numpy as np
import matplotlib.pyplot as plt
from google.colab import files
from PIL import Image

# Função para carregar a imagem
def upload_image():
    uploaded = files.upload()
    for fn in uploaded.keys():
        return Image.open(fn)

# Função para converter imagem colorida para níveis de cinza
def rgb_to_gray(image):
    gray_image = np.dot(np.array(image)[..., :3], [0.2989, 0.5870, 0.1140])
    return gray_image.astype(np.uint8)

# Função para binarizar a imagem
def binarize_image(gray_image, threshold=128):
    binary_image = (gray_image > threshold) * 255
    return binary_image.astype(np.uint8)

# Função para visualizar as imagens
def display_images(original, gray, binary):
    plt.figure(figsize=(15, 5))
    plt.subplot(1, 3, 1)
    plt.imshow(original)
    plt.title('Imagem Original')
    plt.axis('off')

    plt.subplot(1, 3, 2)
    plt.imshow(gray, cmap='gray')
    plt.title('Imagem em Níveis de Cinza')
    plt.axis('off')

    plt.subplot(1, 3, 3)
    plt.imshow(binary, cmap='gray')
    plt.title('Imagem Binarizada')
    plt.axis('off')
    plt.show()

# Executando o código
original_image = upload_image()
gray_image = rgb_to_gray(original_image)
binary_image = binarize_image(gray_image)

# Exibindo as imagens
display_images(original_image, gray_image, binary_image)


# Tecnologias Utilizadas
Python
NumPy
Matplotlib
PIL (Pillow)
Google Colab
