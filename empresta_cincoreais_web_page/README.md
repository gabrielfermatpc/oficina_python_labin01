# Como Criar e Hospedar o Site "Me empresta 5 reais"

Este guia explica como criar um site simples com HTML, CSS e JavaScript, e hospedá-lo no **Netlify**.

---

## Estrutura do Projeto
Organize os arquivos do projeto da seguinte forma:
```
projeto/
│
├── index.html
├── style.css
```

### 1. Arquivo `index.html`
Crie o arquivo **index.html** com o seguinte conteúdo:

```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Me empresta 5 reais</title>
    <link rel="stylesheet" href="style.css"> <!-- Importa o arquivo CSS -->
</head>
<body>
    <h1 id="titulo">Me empresta 5 reais?</h1>
    <div class="botoes">
        <button id="sim" onclick="agradecer()">Sim</button>
        <button id="nao" onclick="moverNao()">Não</button>
    </div>

    <script>
        function moverNao() {
            const naoButton = document.getElementById("nao");
            const newX = Math.floor(Math.random() * (window.innerWidth - 100));
            const newY = Math.floor(Math.random() * (window.innerHeight - 50));
            naoButton.style.position = "absolute";
            naoButton.style.left = `${newX}px`;
            naoButton.style.top = `${newY}px`;
        }

        function agradecer() {
            document.getElementById("titulo").innerText = "Muito obrigado!";
            document.body.style.backgroundColor = "green";

            const msg = document.createElement("p");
            msg.innerText = "Pode confiar que eu devolvo!";
            msg.style.fontSize = "20px";
            msg.style.marginTop = "20px";
            document.body.appendChild(msg);

            document.querySelector(".botoes").style.display = "none";
        }
    </script>
</body>
</html>
```

### 2. Arquivo `style.css`
Crie o arquivo **style.css** para estilizar a página:

```css
/* Estilos gerais */
body {
    background-color: black;
    color: white;
    text-align: center;
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

/* Título */
#titulo {
    margin-bottom: 20px;
    font-size: 24px;
}

/* Container dos botões */
.botoes {
    display: flex;
    gap: 20px; /* Espaço entre os botões */
}

/* Botões */
button {
    font-size: 16px;
    padding: 10px 20px;
    border: none;
    cursor: pointer;
}

/* Botão "Não" */
#nao {
    background-color: red;
    color: white;
}

/* Botão "Sim" */
#sim {
    background-color: green;
    color: white;
}
```

---

## Passo a Passo para Hospedar no Netlify

### 1. Crie uma Conta no Netlify
- Acesse [Netlify](https://www.netlify.com/) e crie uma conta (pode usar o GitHub, Google ou e-mail).

### 2. Faça o Upload do Projeto
Existem duas opções para hospedar o projeto:

#### **Opção 1: Arrastar e Soltar**
1. Compacte os arquivos em uma pasta chamada `projeto`.
2. Acesse o painel do Netlify.
3. Arraste a pasta diretamente para a seção **"Drag and Drop your site folder here"**.

#### **Opção 2: Usar GitHub**
1. Suba os arquivos `index.html` e `style.css` para um repositório no GitHub.
2. No painel do Netlify:
   - Clique em **"New Site from Git"**.
   - Conecte sua conta GitHub e selecione o repositório.
3. Netlify fará o deploy automaticamente.

### 3. Acesse o Link
Após o deploy, o Netlify fornecerá um **link público** (ex.: `https://seusite.netlify.app`).
Você pode compartilhar este link com qualquer pessoa.

---

## Resultado Esperado
- **Botão "Sim"**: Ao clicar, a página exibe uma mensagem de agradecimento e remove os botões.
- **Botão "Não"**: O botão se moverá para uma posição aleatória na tela.
- O site funciona em qualquer navegador moderno e dispositivos móveis.

---

## Tecnologias Utilizadas
- **HTML**: Estrutura da página.
- **CSS**: Estilização da página.
- **JavaScript**: Funcionalidade dinâmica dos botões.
- **Netlify**: Hospedagem gratuita do site.

---

## Licença
Este projeto é de domínio público. Sinta-se à vontade para modificá-lo e compartilhá-lo!
