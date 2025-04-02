# Integrando a IA do Google(Gemini) com o NodeJS 

## Introdução

Este repositório contém uma aplicação em Node.js que utiliza a API do Google Generative AI para responder perguntas sobre destinos turísticos. O projeto está dividido em vários arquivos JavaScript que lidam com diferentes funcionalidades, como perguntas sobre destinos, análises de sentimentos a partir de arquivos de texto, processamento de imagens e comparações entre destinos.

## Estrutura do Projeto

A estrutura do repositório contém os seguintes arquivos principais:

- **scripts-versions/script01.js**: Script que interage com o modelo Gemini para gerar respostas baseadas em uma pergunta sobre um destino de viagem.
- **scripts-versions/script02.js**: Similar ao `script01.js`, mas com categorias de destino, como pontos turísticos, cultura, clima, etc.
- **scripts-versions/script03.js**: Oferece opções para fazer uma pergunta livre sobre um destino ou realizar comparações entre destinos.
- **categorizador.js**: Realiza análise de sentimentos a partir de um arquivo de texto contendo opiniões sobre destinos turísticos.
- **consultaDestino.js**: Script utilizado para consultar destinos turísticos com base em categorias fornecidas pelo usuário.
- **index.js**: Arquivo principal que oferece um menu interativo para o usuário escolher entre várias opções de funcionalidades.
- **modelo.js**: Responsável por inicializar o modelo do Google Generative AI com a chave de API.
- **pergunta.js**: Utilizado para fazer perguntas ao usuário via terminal.
- **perguntaLivre.js**: Gerencia perguntas livres sobre destinos turísticos, utilizando o modelo generativo.
- **processaImagem.js**: Permite ao usuário enviar uma imagem e obter informações sobre o destino mostrado nela.
- **img/**: Nesse diretório você pode armazenar imagens de destinos turísticos, como exemplo, para que o modelo retorne informações sobre esse local.
- **txt/**: Nesse diretório você pode armazenar arquivos de textos para simular pesquisas de avaliação de lugares visitados para análise de sentimentos.

## Requisitos

1. **Node.js:** A aplicação foi desenvolvida utilizando o Node.js. Certifique-se de ter o Node.js instalado na versão 18 ou superior. Você pode verificar se já possui o Node.js com o comando:
   ```bash
   node -v
   ```

2. **Chave da API:** Para esse projeto será necessário criar uma chave de API para integrar o nossa aplicação com a API do Gemini. Acesse a página de chaves de [API do Google AI Studio](https://aistudio.google.com/app/apikey) e clique no botão Create API Key para gerar uma nova chave. Copie a chave que foi gerada.

## Passos para Configuração

### 1. Instalação das Dependências
Primeiro, faça o clone do repositório ou baixe os arquivos. Em seguida, instale as dependências do projeto:

```bash
npm install
```

### 2. Configuração da Chave de API do Google
A chave da API do Google Generative AI deve ser configurada como uma variável de ambiente. Siga as instruções abaixo:
- **Windows** - Basta executar o seguinte comando no terminal do VSCode: `set GEMINI_API_KEY=COLE_SUA_CHAVE_AQUI`
- **Linux ou MacOS** - Basta executar o seguinte comando no terminal: `export GEMINI_API_KEY=COLE_SUA_CHAVE_AQUI`

**OBS: Você pode também criar um arquivo `.env` na raiz do seu projeto e adicionar a seguinte linha:**

```bash
GEMINI_API_KEY=SuaChaveDeAPIAqui
```

### 3. Executando o Projeto
Para rodar o projeto, basta executar o arquivo `index.js`, que oferece um menu interativo para o usuário escolher entre as opções de funcionalidades.

```bash
node index.js
```

Após isso, o programa apresentará opções para o usuário escolher entre perguntas sobre destinos, comparação de destinos, análise de sentimentos de textos e mais.

### 4. Personalizando as Perguntas

#### Arquivo `script01.js` e `script02.js`
Nos arquivos `script01.js` e `script02.js`, você pode alterar o `prompt` e as perguntas feitas ao usuário. O prompt é a introdução que descreve o comportamento do modelo. Modifique a parte onde é definido o prompt para mudar o comportamento da aplicação. Exemplo:

```javascript
let prompt = "Você é um especialista em viagens e deve responder sobre qualquer destino turístico." +
  " Caso o usuário pergunte sobre algo diferente, diga que não pode responder. " +
  " O usuário escolheu: ";
```

Se quiser personalizar as perguntas feitas ao usuário, altere os textos dentro do `fazerPergunta`:

```javascript
const prompt = await fazerPergunta("Qual destino você deseja conhecer?");
```

#### Arquivo `perguntaLivre.js`
Neste arquivo, o usuário pode fazer perguntas livres sobre um destino. Personalize o prompt para ajustar a forma como o modelo responderá:

```javascript
const prompt = await fazerPergunta("Me faça uma pergunta sobre um destino turístico.");
```

#### Arquivo `consultaDestino.js`
Para customizar as categorias de informações sobre o destino, altere o prompt de categorias no arquivo `consultaDestino.js`:

```javascript
const categorias = await fazerPergunta("Me fale as categorias que deseja visualizar sobre um destino, como pontos turísticos, clima, cultura...");
```

## Funcionalidades

1. **Fazer Perguntas Livres**: O usuário pode fazer perguntas sobre destinos turísticos, e o modelo responderá com informações baseadas no seu treinamento.
2. **Comparação de Destinos**: O usuário pode comparar diferentes destinos com base nas categorias que ele escolher, como clima, pontos turísticos, culinária, etc.
3. **Análise de Sentimentos (Arquivo de Texto)**: O modelo analisa um arquivo de texto contendo opiniões sobre destinos turísticos e categoriza as respostas em "satisfeito", "insatisfeito" ou "neutro".
4. **Processamento de Imagem**: O usuário pode enviar uma imagem de um destino turístico, e o modelo retornará informações sobre esse local.

## Personalização de Funções
Você pode facilmente personalizar o comportamento do aplicativo editando os arquivos conforme necessário:

- **Alterar o modelo do Google Generative AI**: Se você quiser usar um modelo diferente, altere a linha onde o modelo é inicializado, por exemplo, no arquivo `modelo.js`:

  ```javascript
  const model = genAI.getGenerativeModel({ model: "gemini-1.0-pro" });
  ```

- **Alterar Perguntas e Prompts**: Em todos os arquivos, você pode personalizar o texto da pergunta ou do prompt de entrada para melhor se adequar ao seu caso de uso.

## Contribuições
Contribuições são bem-vindas! Se você quiser melhorar o projeto, sinta-se à vontade para fazer um fork e enviar pull requests. Certifique-se de testar suas alterações antes de submeter.

## Licença
Este projeto está licenciado sob a Licença MIT - consulte o arquivo [LICENSE](LICENSE) para mais detalhes.
