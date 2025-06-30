Claro! Aqui está um **passo a passo completo** para você documentar no GitHub (README ou qualquer tutorial) **como criar e publicar uma página com PDF + Assistente Virtual do Copilot (Power Virtual Agents)**, usando **GitHub Pages**:

---

## 🛠️ **Passo a passo: Publicar Assistente Virtual + PDF via GitHub Pages**

### 🔹 1. Criar o bot no Copilot Studio (Microsoft)

1. Acesse: [https://copilotstudio.microsoft.com](https://copilotstudio.microsoft.com)
2. Crie um bot com nome e idioma desejado
3. Vá em **Tópicos** e crie os fluxos com base em sua Carta de Serviços
4. Nas respostas que devem abrir o PDF, adicione um link como:

```
📄 [Clique aqui para visualizar o documento](#abrir-pdf)
```

---

### 🔹 2. Ativar o canal "Website" e copiar o iframe

1. No menu esquerdo do bot, clique em **"Canais"**
2. Vá em **"Website"**
3. Copie o código do tipo:

```html
<iframe src="https://copilotstudio.microsoft.com/environments/Default-xxx/bots/xxx/webchat?__version__=2"></iframe>
```

⚠️ Copie apenas o link de `src`, pois usaremos no HTML.

---

### 🔹 3. Criar estrutura de projeto

No GitHub, crie um repositório e envie estes arquivos para a **raiz** (sem subpastas):

```
📁 assistente-virtual-saa/
├── index.html               ← Página principal
└── carta-servicos-saa.pdf   ← Arquivo PDF
```

---

### 🔹 4. Código do `index.html`

Substitua o `src` do iframe com o link do seu bot:

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Assistente Virtual + PDF</title>
  <style>
    html, body {
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', sans-serif;
      height: 100%;
    }

    iframe#pdf-frame {
      width: 100%;
      height: 90vh;
      display: none;
      border: none;
    }

    #botao-chat {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background: #0078D4;
      color: white;
      padding: 12px 18px;
      border: none;
      border-radius: 25px;
      font-size: 14px;
      cursor: pointer;
      z-index: 1000;
      box-shadow: 0 4px 12px rgba(0,0,0,0.2);
    }

    #chatbox {
      display: none;
      position: fixed;
      bottom: 80px;
      right: 20px;
      width: 400px;
      height: 600px;
      border-radius: 10px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.2);
      overflow: hidden;
      z-index: 999;
      border: 1px solid #ccc;
    }

    #chatbox-header {
      background-color: #0b556a;
      color: white;
      padding: 12px;
      font-weight: bold;
      text-align: center;
      position: relative;
    }

    #fechar-chat {
      position: absolute;
      top: 8px;
      right: 12px;
      background: transparent;
      border: none;
      color: white;
      font-size: 18px;
      cursor: pointer;
    }

    #chat-iframe {
      width: 100%;
      height: calc(100% - 48px);
      border: none;
    }
  </style>
</head>
<body>

  <!-- PDF -->
  <iframe id="pdf-frame" src="carta-servicos-saa.pdf#toolbar=0"></iframe>

  <!-- Chatbox -->
  <div id="chatbox">
    <div id="chatbox-header">
      Assistente Virtual da Subsecretaria de Assuntos Administrativos - SAA
      <button id="fechar-chat" onclick="fecharChat()">×</button>
    </div>
    <iframe
      id="chat-iframe"
      src="https://copilotstudio.microsoft.com/environments/Default-xxx/bots/xxx/webchat?__version__=2">
    </iframe>
  </div>

  <button id="botao-chat" onclick="abrirChat()">💬 Assistente Virtual</button>

  <script>
    function abrirChat() {
      document.getElementById("chatbox").style.display = "block";
    }

    function fecharChat() {
      document.getElementById("chatbox").style.display = "none";
    }

    // Mostrar PDF se o link tiver o hash #abrir-pdf
    window.addEventListener("hashchange", function () {
      if (location.hash === "#abrir-pdf") {
        const pdf = document.getElementById("pdf-frame");
        pdf.style.display = "block";
        pdf.scrollIntoView({ behavior: "smooth" });
      }
    });
  </script>
</body>
</html>
```

---

### 🔹 5. Ativar o GitHub Pages

1. Vá no repositório
2. Clique em **Settings > Pages**
3. Em “Source”, escolha:

   * Branch: `main` (ou `principal`)
   * Folder: `/ (root)`
4. Clique em **Salvar**

O GitHub vai gerar um link como:

```
https://seuusuario.github.io/assistente-virtual-saa/
```

---

### ✅ Teste final

1. Acesse o link do GitHub Pages
2. Clique em 💬 Assistente Virtual
3. Envie uma pergunta
4. Quando o bot responder com link para `#abrir-pdf`, o PDF será exibido automaticamente.

---

Se quiser, posso exportar esse passo a passo em `.md` para você colocar no README.md. Deseja?
