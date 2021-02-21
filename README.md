####  Bootcamp - GoStack 11
# 🚀 Nível 03 - Iniciando Front-End Web (GoBarber Web)

## Sobre

- Durante esse módulo criaremos a versão web da aplicação GoBarber que será utilizada pelos usuários que prestam serviços dentro da aplicação
- A aplicação irá consumir a API Back-end Node.js abaixo
  - [Back-end - GoBarber](https://github.com/fabiosvf/bootcamp-gostack-11-nivel-02-iniciando-back-end-do-app)

---
## Roteiro

- Nesta seção será descrito o roteiro com todos os passos para criação do projeto em ReactJS com TypeScript

### Criando o projeto
- Crie uma pasta
- Acesse a pasta em modo terminal
- Digite o seguinte comando para iniciar o projeto à partir de um template padrão contendo várias ferramentas como Babbel e WebPack já configuradas:
```
$ yarn create react-app nome-do-projeto --template typescript
```
- Abra a pasta do projeto no Visual Studio Code
```
$ code .
```
### Configurando a versão inicial do projeto
- Apague os seguintes arquivos que foram gerados automaticamente à partir do comando `create react_app`
```
public\favicon.ico
public\logo192.png
public\logo512.png
public\manifest.json
src\App.css
src\App.test.tsx
src\index.css
src\logo.svg
src\reportWebVitals.ts
```
- Acesse o arquivo `public\index.html` e mantenha o seguinte código:
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <meta name="theme-color" content="#3A3A3A" />
    <title>GoBarber Web</title>
  </head>
  <body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="root"></div>
  </body>
</html>
```
- Acesse o arquivo `src\App.tsx` e mantenha o seguinte código:
```ts
import React from 'react';

function App() {
  return (
    <h1>Hello World</h1>
  );
}

export default App;
```
- Acesse o arquivo `src\index.tsx` e mantenha o seguinte código:
```ts
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);
```
### Configurando padrões de projeto com ESLint, Prettier e EditorConfig

#### Configurando o EditorConfig
- Instale a extensão `EditorConfig for VS Code` no Visual Studio Code
- Crie o arquivo `.editorconfig` na raiz do projeto com o seguinte conteúdo:
```
root = true

[*]
indent_style = space
indent_size = 2
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true
end_of_line = lf
```

#### Configurando o ESLint
- Instale a extensão `ESLint` no Visual Studio Code
- Abra o arquivo `settings.json` pressionando `CTRL + P` e digitando o nome do arquivo.
- Adicione o trecho abaixo no final do arquivo:
```
"editor.codeActionsOnSave": {
  "source.fixAll.eslint": true
}
```
- Abra o arquivo `package.json` localizado na raiz do projeto
- Localize e remova o seguinte trecho de configuração:
```
  "eslintConfig": {
    "extends": [
      "react-app",
      "react-app/jest"
    ]
  },
```
- Instale a biblioteca `eslint` como dependência de desenvolvimento:
```
$ yarn add eslint -D
```
- Inicie o assistente de configuração do ESLint digitando o seguinte comando:
```
$ yarn eslint --init
```
- Responda as perguntas com as seguintes informações:
  - How would you like to use ESLint? `To check syntax, find problems, and enforce code style`
  - What type of module does your project use? `JavaScrtipt modules (import/export)`
  - Which framework does your project use? `React`
  - Does your project use TypeScript? `Yes`
  - Where does your code run? `Browser`
  - How would you like to define a style for your project? `Use a popular style guide`
  - Which style guide do you want to foloow? `Airbnb: https://github.com/airbnb/javascript`
  - What format do you want your config file to be in? `JSON`
  - Would you like to install them now with npm? `No`
- Copie as linhas de comando sugeridas pelo assistente para realizar a instalação das bibliotecas de forma manual
  - No meu caso, as bibliocas sugeridas para instalação foram:
```
eslint-plugin-react@^7.21.5 @typescript-eslint/eslint-plugin@latest eslint-config-airbnb@latest eslint@^5.16.0 || ^6.8.0 || ^7.2.0 eslint-plugin-import@^2.22.1 eslint-plugin-jsx-a11y@^6.4.1 eslint-plugin-react-hooks@^4 || ^3 || ^2.3.0 || ^1.7.0 @typescript-eslint/parser@latest
```
- Remova, da sugestão de instalação, a referência completa à instalação da biblioteca `eslint`. No meu caso são essas versões:
```
eslint@^5.16.0 || ^6.8.0 || ^7.2.0
```
- Remova, da sugestão de instalação, a referência à versões anteriores para a biblioteca `eslint-plugin-react-hooks` e mantenha apenas a versão mais atual
```
De
eslint-plugin-react-hooks@^4 || ^3 || ^2.3.0 || ^1.7.0
Para
eslint-plugin-react-hooks@^4
```
- Instale as bibliotecas manualmente
```
yarn add -D eslint-plugin-react@^7.21.5 @typescript-eslint/eslint-plugin@latest eslint-config-airbnb@latest eslint-plugin-import@^2.22.1 eslint-plugin-jsx-a11y@^6.4.1 eslint-plugin-react-hooks@^4 @typescript-eslint/parser@latest
```
- Crie o arquivo `.eslintignore` na raiz do projeto com o seguinte conteúdo:
```
**/*.js
node_modules
build
/src/react-app-env.d.ts
/src/reportWebVitals.ts
```
- Na raiz do projeto, localize o arquivo `.eslintrc.json` e dentro da sessão `extends` adicione o seguinte trecho de código:
```
"plugin:@typescript-eslint/recommended"
```
- Ainda no arquivo `.eslintrc.json` adicione o seguinte código dentro da sessão `plugins`:
```
"react-hooks"
```
- Para finalizar o ajuste no arquivo `.eslintrc.json` adicione o código abaixo dentro da sessão `rules`:
```
"react-hooks/rules-of-hooks": "error",
"react-hooks/exhaustive-deps": "warn",
"react/jsx-filename-extension": [
	1,
	{
	"extensions": [
		".tsx"
	]
	}
],
"no-use-before-define": "off",
"@typescript-eslint/no-use-before-define": [
	"error"
],
"react/react-in-jsx-scope": "off"
```
- Instale a biblioteca `eslint-import-resolver-typescript` como dependência de desenvolvimento:
```
$ yarn add eslint-import-resolver-typescript -D
```
- Abra novamente o arquivo de configuração `.eslintrc.json` e adicione o seguinte código na sessão `rules`:
```
"import/extensions": [
    "error",
    "ignorePackages",
    {
      "ts": "never",
      "tsx": "never"
    }
 ]
```
- Ainda no arquivo `.eslintrc.json`, logo abaixo da sessão `rules` adicione o seguinte código:
```
"settings": {
    "import/resolver": {
      "typescript": {}
    }
  }
```

#### Configurando o Prettier
- Desinstale a extensão `Prettier - Code Formatter` caso a mesma esteja instalada
- Instale as seguintes bibliotecas como dependências de desenvolvimento:
```
$ yarn add prettier eslint-config-prettier eslint-plugin-prettier -D
```
- Na sessão `extends` do arquivo de configuração `.eslintrc.json` adicione o seguinte código:
```
"prettier/@typescript-eslint",
"plugin:prettier/recommended"
```
- Ainda no mesmo arquivo de configuração adicione o seguinte código na sessão `rules`:
```
"prettier/prettier": "error"
```
- O código final do arquivo `.eslintrc.json` deverá ficar parecido com o conteúdo abaixo:
```json
{
    "env": {
        "browser": true,
        "es2021": true
    },
    "extends": [
        "plugin:react/recommended",
        "airbnb",
        "plugin:@typescript-eslint/recommended",
        "prettier/@typescript-eslint",
        "plugin:prettier/recommended"
    ],
    "parser": "@typescript-eslint/parser",
    "parserOptions": {
        "ecmaFeatures": {
            "jsx": true
        },
        "ecmaVersion": 12,
        "sourceType": "module"
    },
    "plugins": [
        "react",
        "@typescript-eslint",
        "react-hooks"
    ],
    "rules": {
      "react-hooks/rules-of-hooks": "error",
      "react-hooks/exhaustive-deps": "warn",
      "react/jsx-filename-extension": [
        1,
        {
        "extensions": [
          ".tsx"
        ]
        }
      ],
      "no-use-before-define": "off",
      "@typescript-eslint/no-use-before-define": [
        "error"
      ],
      "react/react-in-jsx-scope": "off",
      "import/extensions": [
        "error",
        "ignorePackages",
        {
          "ts": "never",
          "tsx": "never"
        }
     ],
     "prettier/prettier": "error"
    },
    "settings": {
      "import/resolver": {
        "typescript": {}
      }
    }
}
```
- Crie o arquivo `prettier.config.js` na raiz do projeto e adicione o seguinte código:
```
module.exports = {
  singleQuote: true,
  trailingComma: 'all',
	arrowParens: 'avoid',
}
```
- Crie ou edite o arquivo `.eslintignore` na raiz do projeto e adicione a seguinte regra:
```
/*.js
```
### Estrutura das páginas

#### Estilos globais
- Instale a biblioteca `styled-components`
```
$ yarn add styled-components
```
- Instale a biblioteca `@types/styled-components` como dependência de desenvolvimento
```
$ yarn add @types/styled-components -D
```
- Instale a extensão `vcode-styled-components` no Visual Studio Code
- Acesse o site [Google Fonts](https://fonts.google.com/), localize a fonte `Roboto Slab`, selecione os estilos `Regular 400` e `Medium 500`, em seguida, na lateral direita, copie o link gerado automaticamente e cole dentro da tag `head` abaixo da tag `title` dentro do arquivo `public/index.html`
```
<link href="https://fonts.googleapis.com/css2?family=Roboto+Slab:wght@400;500&family=Roboto:wght@400;500&display=swap" rel="stylesheet">
```
- Abra o arquivo `.eslintrc.json` na raiz do projeto, localize a sessão `rules` e adicione o parâmetro abaixo:
  - Esse parâmetro desativa a obrigatoriedade em definir um `export default`. Esse recurso é importante quando trabalhamos com `styled-components` pois podemos exportar vários estilos em um único arquivo onde nenhum, em específico, será `default`.
```
"import/prefer-default-export": "off"
```
#### Página de login
- Instale a biblioteca `react-icons`
```
$ yarn add react-icons
```
- Instale a biblioteca `polished`
```
$ yarn add polished
```
#### Isolando componentes
- Abra o arquivo `.eslintrc.json` localize a sessão `rules` e acrescente a seguinte regra:
  - Caso insira os parâmetros no final das regras, então remova a última vírgula.
  - O primeiro parâmetro foi desabilitado para permitir passar `props` para um componente
  - O segundo parâmetro desabilita a necessidade de implementar a tipagem `prop-types` porque o `typescript` já está responsável por isso
```
"react/jsx-props-no-spreading": "off",
"react/prop-types": "off",
```
#### Utilizando Unform
- Instale as bibliotecas `@unform/core` e `@unform/web`
```
$ yarn add @unform/core @unform/web
```
#### Validando cadastro
- Instale a biblioteca `yup`
```
$ yarn add yup
```
- Instale a biblioteca `@types/yup` como dependência de desenvolvimento
```
$ yarn add @types/yup -D
```
#### Exibindo erros no Input
- Abra o arquivo `.eslintrc.json` localize a sessão `rules` e adicione o seguinte parâmetro
  - Essa regra foi desabilitada, porque em alguns momentos, o `eslint` confunde o caracter `?` como um `if ternário` ao invés de `property nullable`
```
"no-unused-expressions": "off",
```
### Autenticação
#### Login pelo Contexto
- Instale a biblioteca `axios`
```
$ yarn add axios
```
---
## Padrões de Projeto

#### Introdução
- [Padrões de projeto com ESLint, Prettier e EditorConfig](docs/Padr%C3%B5es%20de%20projeto%20com%20ESLint%2C%20Prettier%20e%20EditorConfig.pdf)

#### Ferramentas para padronização de código
- [EditorConfig](docs/EditorConfig.pdf)
- [ESLint](docs/ESLint.pdf)
- [Prettier](docs/Prettier.pdf)

#### React Hooks e Context API
- [React Hooks e Context API](docs/ReactHooksContextAPI.pdf)
---

## Tecnologias utilizadas

#### Dependências de Projeto
- [@testing-library/jest-dom](https://yarnpkg.com/package/@testing-library/jest-dom)
- [@testing-library/react](https://yarnpkg.com/package/@testing-library/react)
- [@testing-library/user-event](https://yarnpkg.com/package/@testing-library/user-event)
- [@types/jest](https://yarnpkg.com/package/@types/jest)
- [@types/node](https://yarnpkg.com/package/@types/node)
- [@types/react](https://yarnpkg.com/package/@types/react)
- [@types/react-dom](https://yarnpkg.com/package/@types/react-dom)
- [@unform/core](https://yarnpkg.com/package/@unform/core)
- [@unform/web](https://yarnpkg.com/package/@unform/web)
- [axios](https://yarnpkg.com/package/axios)
- [polished](https://yarnpkg.com/package/polished)
- [react](https://yarnpkg.com/package/react)
- [react-dom](https://yarnpkg.com/package/react-dom)
- [react-icons](https://yarnpkg.com/package/react-icons)
- [react-scripts](https://yarnpkg.com/package/react-scripts)
- [styled-components](https://yarnpkg.com/package/styled-components)
- [typescript](https://yarnpkg.com/package/typescript)
- [web-vitals](https://yarnpkg.com/package/web-vitals)
- [yup](https://yarnpkg.com/package/yup)

#### Dependências de Desenvolvimento
- [@types/styled-components](https://yarnpkg.com/package/@types/styled-components)
- [@types/yup](https://yarnpkg.com/package/@types/yup)
- [@typescript-eslint/eslint-plugin](https://yarnpkg.com/package/@typescript-eslint/eslint-plugin)
- [@typescript-eslint/parser](https://yarnpkg.com/package/@typescript-eslint/parser)
- [eslint](https://yarnpkg.com/package/eslint)
- [eslint-config-airbnb](https://yarnpkg.com/package/eslint-config-airbnb)
- [eslint-config-prettier](https://yarnpkg.com/package/eslint-config-prettier)
- [eslint-import-resolver-typescript](https://yarnpkg.com/package/eslint-import-resolver-typescript)
- [eslint-plugin-import](https://yarnpkg.com/package/eslint-plugin-import)
- [eslint-plugin-jsx-a11y](https://yarnpkg.com/package/eslint-plugin-jsx-a11y)
- [eslint-plugin-prettier](https://yarnpkg.com/package/eslint-plugin-prettier)
- [eslint-plugin-react](https://yarnpkg.com/package/eslint-plugin-react)
- [eslint-plugin-react-hooks](https://yarnpkg.com/package/eslint-plugin-react-hooks)
- [prettier](https://yarnpkg.com/package/prettier)
---

## Como executar
- Crie uma pasta para o projeto
- Acesse a pasta
- Faça o clone do projeto
```
$ git clone https://github.com/fabiosvf/bootcamp-gostack-11-nivel-03-iniciando-front-end-web.git .
```
- Atualize as bibliotecas
```
$ yarn
```
- Para iniciar a aplicação web, digite:
```
$ yarn start
```
