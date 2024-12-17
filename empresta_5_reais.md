# Instruções - Programa Tkinter

## Objetivo
Este programa cria uma interface gráfica simples utilizando **Tkinter** em Python. Ele exibe dois botões, "Sim" e "Não", para uma pergunta divertida. O botão "Não" se move para uma posição aleatória quando clicado, enquanto o botão "Sim" agradece e fecha o programa.

---

## Estrutura do Código

### 1. Importação de Bibliotecas
```python
import tkinter as tk
import random
```
- **tkinter**: Biblioteca padrão do Python para GUIs.
- **random**: Gera números aleatórios.

### 2. Função `mover_nao()`
```python
def mover_nao():
    novo_x = random.randint(0, janela.winfo_width() - 100)
    novo_y = random.randint(0, janela.winfo_height() - 50)
    botao_nao.place(x=novo_x, y=novo_y)
```
- Move o botão "Não" para uma posição aleatória dentro da janela.

### 3. Função `agradecer()`
```python
def agradecer():
    label_titulo.config(text="Muito obrigado!", fg="green")
    janela.after(1000, janela.destroy)
```
- Exibe a mensagem **"Muito obrigado!"** e fecha a janela após 1 segundo.

### 4. Configuração da Janela Principal
```python
janela = tk.Tk()
janela.title("Me empresta 5 reais")
janela.geometry("400x300")
janela.configure(background="black")
```
- Cria a janela principal com dimensões fixas e fundo preto.

### 5. Criação do Título
```python
label_titulo = tk.Label(janela, text="Me empresta 5 reais?", font=("Arial", 16), bg="black", fg="white")
label_titulo.pack(pady=20)
```
- Exibe o texto principal da interface.

### 6. Botão "Sim"
```python
botao_sim = tk.Button(janela, text="Sim", font=("Arial", 12), command=agradecer)
botao_sim.place(x=150, y=80)
```
- Ao ser clicado, exibe a mensagem de agradecimento e fecha a janela.

### 7. Botão "Não"
```python
botao_nao = tk.Button(janela, text="Não", font=("Arial", 12), command=mover_nao)
botao_nao.place(x=220, y=80)
```
- Se move aleatoriamente sempre que é clicado.

### 8. Loop Principal
```python
janela.mainloop()
```
- Mantém a janela aberta e processa os eventos.

---

## Resumo
- **Botão "Sim"**: Mostra uma mensagem de agradecimento e fecha o programa.
- **Botão "Não"**: Foge para uma posição aleatória.

**Divirta-se!** 😉
