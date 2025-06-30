# 🤖 Assistente Virtual da Subsecretaria de Assuntos Administrativos – SAA

Este projeto integra a **Carta de Serviços da SAA** em PDF com um **chatbot inteligente** criado no **Microsoft Copilot Studio** e publicado via **GitHub Pages**. O assistente responde **exclusivamente** com base no conteúdo oficial da carta.

---

## 🧠 ETAPA 1: Criar o Agente no Microsoft Copilot Studio

### 1. Acesse o Copilot Studio  
- Visite: https://copilotstudio.microsoft.com  
- Faça login com sua conta institucional (gov.br, saúde.gov.br ou Microsoft 365).

### 2. Crie um novo bot  
1. Clique em **Copilots** (ou **Meus Agentes**)  
2. Clique em **Criar** (ou **Novo copiloto**)  
3. Defina:  
   - **Nome**: `Assistente Virtual SAA`  
   - **Idioma**: Português (Brasil)  
4. Confirme  

### 3. Adicione a base de conhecimento  
- No menu lateral, vá em **Base de conhecimento → Adicionar fonte**  
- Faça **Upload** do PDF da Carta de Serviços **ou** cole o link público (SharePoint, GitHub Pages…)  
- Isso garante que o agente use esse documento para fundamentar as respostas.

### 4. Configure o comportamento da IA  
- Vá em **Configurações > IA Generativa**  
- Adicione este prompt como **comportamento personalizado**:

    ```text
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

    Evite qualquer conteúdo que não esteja presente nas fontes; não invente informações.
    ```

### 5. Teste o agente  
- Clique em **Testar seu copiloto** e faça algumas perguntas para validar o fluxo.

### 6. Publique o bot  
- Vá em **Publicar > Publicar agora**

### 7. Obtenha o link do Webchat  
1. Vá em **Canais > Aplicativo Web**  
2. Ative o canal e copie o URL do iframe, por exemplo:

    ```
    https://copilotstudio.microsoft.com/environments/DEFAULT_ID/bots/BOT_ID/webchat?__version__=2
    ```

> ⚠️ Anote este link, você vai usá-lo em `index.html`.

---

## 🌐 ETAPA 2: Criar a Página Web no GitHub Pages

### 1. Crie o repositório no GitHub  
- Acesse GitHub → **New Repository**  
- Nome sugerido: `assistente-virtual-saa`  
- Marque **Public** e **Add a README file**  
- Clique em **Create repository**

### 2. Prepare os arquivos locais  
Na sua máquina, crie uma pasta `assistente-virtual-saa` com:  
