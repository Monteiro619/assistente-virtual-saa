```
# 🧠 Assistente Virtual da Subsecretaria de Assuntos Administrativos - SAA

Este projeto integra um agente inteligente do **Microsoft Copilot Studio** com uma interface Web contendo a **Carta de Serviços da SAA em PDF**. O chatbot responde exclusivamente com base nas informações oficiais fornecidas.

---

## ✅ ETAPA 1: Criar o Agente no Microsoft Copilot Studio

### 1. Acesse o Copilot Studio
- Vá para: [https://copilotstudio.microsoft.com](https://copilotstudio.microsoft.com)
- Faça login com sua conta institucional (gov.br, saúde.gov.br ou Microsoft 365).

### 2. Crie um novo bot
- Vá em **Copilots** ou **Meus Agentes**
- Clique em **Criar**
- Defina um nome: `Assistente Virtual SAA`
- Idioma: `Português (Brasil)`
- Confirme

### 3. Adicione a base de conhecimento
- No menu lateral, vá para: **Base de conhecimento → Adicionar fonte**
- Faça o upload do arquivo PDF da **Carta de Serviços**
- Ou adicione um link público do PDF (por exemplo, do GitHub Pages ou SharePoint)
- Isso permite que o agente responda com base nesse conteúdo

### 4. Configure o comportamento da IA
- Vá em **Configurações > IA generativa**
- Adicione um comportamento personalizado com o seguinte conteúdo:

```

Use exclusivamente as fontes de conhecimento fornecidas para responder às perguntas.

Sempre organize a resposta neste formato:

Serviço:
Macroprocesso:
Unidade responsável:
Contato:
O que é?
Quem pode solicitar?
Como solicitar?
Tempo médio de atendimento:

Se a informação solicitada não estiver disponível, responda:
“Desculpe, não encontrei essa informação na Carta de Serviços.”

Evite qualquer conteúdo que não esteja presente nas fontes, não invente informações.

```

### 5. Teste e publique o bot
- Vá em **Testar seu copiloto** para validar as respostas
- Depois, clique em **Publicar > Publicar agora**

### 6. Obtenha o link do Webchat
- Vá em **Canais > Aplicativo Web**
- Ative o canal e copie o link gerado. Ele terá a seguinte estrutura:

```

[https://copilotstudio.microsoft.com/environments/SEU\_ID/bots/SEU\_ID/webchat?\_\_version\_\_=2](https://copilotstudio.microsoft.com/environments/SEU_ID/bots/SEU_ID/webchat?__version__=2)

```

Copie esse link para usar na interface da página.

---

## 🌐 ETAPA 2: Criar a Página Web no GitHub Pages

### 1. Estrutura do repositório

Crie um repositório no GitHub com o nome:

```

assistente-virtual-saa

```

Adicione os seguintes arquivos:

```

assistente-virtual-saa/
├── index.html
├── carta-servicos-saa.pdf.pdf
└── README.md

```

### 2. Interface HTML

O código que exibe o PDF e o botão flutuante do chatbot já está no arquivo `index.html`.

Você só precisa:

- Substituir o link do chatbot (`iframe src`) pelo link copiado do Copilot Studio.
- Garantir que o nome do PDF (`carta-servicos-saa.pdf.pdf`) esteja idêntico ao nome no `src` do iframe.

O layout foi construído com HTML, CSS e JavaScript puro e é responsivo.

### 3. Publicar com GitHub Pages

- Vá para o repositório no GitHub
- Acesse **Settings > Pages**
- Em **Build and Deployment**, selecione:
  - **Branch**: `main` ou `principal`
  - **Diretório**: `/ (root)`
- Clique em **Salvar**

O GitHub Pages irá gerar uma URL como esta:

```

[https://seuusuario.github.io/assistente-virtual-saa/](https://seuusuario.github.io/assistente-virtual-saa/)

```

Acesse o link para ver a página publicada.

---

## ✅ Resultado Final

🔹 A página exibe automaticamente o PDF da Carta de Serviços  
🔹 Um botão no canto inferior direito permite abrir o chatbot  
🔹 O chatbot responde apenas com base no conteúdo da Carta de Serviços

---

## 📎 Observações

- O chatbot **não interage diretamente com o PDF na página** – ele usa a **base carregada no Copilot Studio**.
- O PDF na interface é apenas para visualização manual pelo usuário.
- A interface está otimizada para funcionar bem em desktop e mobile.

---

Desenvolvido para facilitar o acesso a serviços administrativos do Ministério da Saúde.
```

