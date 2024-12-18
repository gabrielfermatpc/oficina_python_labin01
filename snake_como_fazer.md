# Tutorial Passo a Passo: Criando o Jogo da Cobrinha com Pygame

## Introdução
Neste tutorial, você aprenderá a criar o clássico jogo da cobrinha utilizando a biblioteca Pygame. Vamos explorar o código fornecido passo a passo, para que você possa entender e implementar cada parte do jogo.

## Pré-requisitos
Certifique-se de ter o Python instalado em sua máquina. Além disso, instale o Pygame executando:

```bash
pip install pygame
```

## Passo 1: Importando Bibliotecas e Configurando a Tela
Crie um arquivo Python e inicie o código com as configurações básicas:

```python
import pygame
import random

pygame.init()

# Configuração da janela
tela = pygame.display.set_mode((600, 400))
pygame.display.set_caption("Jogo da Cobrinha")
relogio = pygame.time.Clock()

# Cores
preta = (0, 0, 0)
branca = (255, 255, 255)
vermelha = (255, 0, 0)
verde = (0, 255, 0)
```

Aqui, inicializamos o Pygame e configuramos a tela, incluindo a definição de algumas cores básicas.

## Passo 2: Definindo Variáveis e Funções
### Parâmetros da Cobrinha e Funções Auxiliares

Adicione os seguintes códigos para definir parâmetros e criar funções auxiliares:

```python
# Parâmetros
largura, altura = 600, 400
tamanho_do_quadrado = 20
velocidade_jogo = 5

def gerar_comida():
    comida_x = round(random.randrange(0, largura - tamanho_do_quadrado) / 20.0) * 20.0
    comida_y = round(random.randrange(0, altura - tamanho_do_quadrado) / 20.0) * 20.0
    return comida_x, comida_y

def desenhar_comida(tamanho, comida_x, comida_y):
    pygame.draw.rect(tela, verde, [comida_x, comida_y, tamanho, tamanho])

def desenhar_cobra(tamanho, pixels):
    for pixel in pixels:
        pygame.draw.rect(tela, branca, [pixel[0], pixel[1], tamanho, tamanho])

def desenhar_pontuação(pontuação):
    fonte = pygame.font.SysFont("Helvetica", 35)
    texto = fonte.render(f"Pontos: {pontuação}", True, vermelha)
    tela.blit(texto, [1, 1])
```

Essas funções permitem gerar comida aleatoriamente, desenhar a comida, desenhar a cobra e exibir a pontuação.

## Passo 3: Controlando a Cobra
Adicione uma função para definir a direção da cobra com base nas teclas pressionadas:

```python
def selecionar_velocidade(tecla):
    if tecla == pygame.K_DOWN:
        velocidade_x = 0
        velocidade_y = tamanho_do_quadrado
    elif tecla == pygame.K_UP:
        velocidade_x = 0
        velocidade_y = -tamanho_do_quadrado
    elif tecla == pygame.K_LEFT:
        velocidade_x = -tamanho_do_quadrado
        velocidade_y = 0
    elif tecla == pygame.K_RIGHT:
        velocidade_x = tamanho_do_quadrado
        velocidade_y = 0
    return velocidade_x, velocidade_y
```

## Passo 4: Criando a Função Principal
Adicione a lógica principal do jogo:

```python
def rodar_jogo():
    fim_jogo = False

    # Inicializando posição e velocidade da cobra
    x = largura / 2
    y = altura / 2
    velocidade_x = 0
    velocidade_y = 0

    # Inicializando a cobra e a comida
    tamanho_cobra = 1
    pixels = []
    comida_x, comida_y = gerar_comida()

    while not fim_jogo:
        tela.fill(preta)

        for evento in pygame.event.get():
            if evento.type == pygame.QUIT:
                fim_jogo = True
            elif evento.type == pygame.KEYDOWN:
                velocidade_x, velocidade_y = selecionar_velocidade(evento.key)

        # Atualizar posição da cobra
        x += velocidade_x
        y += velocidade_y

        # Verificar colisões
        if x < 0 or x >= largura or y < 0 or y >= altura:
            fim_jogo = True

        # Atualizar a cobra
        pixels.append([x, y])
        if len(pixels) > tamanho_cobra:
            del pixels[0]

        for pixel in pixels[:-1]:
            if pixel == [x, y]:
                fim_jogo = True

        # Verificar se a cobra comeu a comida
        if x == comida_x and y == comida_y:
            tamanho_cobra += 1
            comida_x, comida_y = gerar_comida()

        # Desenhar elementos
        desenhar_comida(tamanho_do_quadrado, comida_x, comida_y)
        desenhar_cobra(tamanho_do_quadrado, pixels)
        desenhar_pontuação(tamanho_cobra - 1)
        pygame.display.update()

        relogio.tick(velocidade_jogo)

    pygame.quit()

rodar_jogo()
```

## Passo 5: Executando o Jogo
Salve o arquivo e execute-o com:

```bash
python nome_do_arquivo.py
```

## Explicação das Funcionalidades
1. **Tela:** Configurada para 600x400 pixels.
2. **Cores:** Usadas para desenhar a comida, cobra e pontuação.
3. **Movimento:** Controlado pelas teclas de seta.
4. **Colisões:** Fim de jogo ocorre ao colidir com as bordas ou com o próprio corpo.
5. **Pontuação:** Aumenta quando a cobra come a comida.

Agora você tem um jogo da cobrinha funcional! Experimente ajustar os parâmetros como velocidade e tamanho para personalizá-lo.

