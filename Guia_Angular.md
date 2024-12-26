# Guia de Configuração para Trabalhar com Angular

## 1. Instalar Node.js e npm
O Angular requer o Node.js e o npm para gerenciar pacotes e executar seus scripts.

- **Baixe e instale o Node.js:** [Node.js Download](https://nodejs.org/)
- **Verifique a instalação:**
  ```bash
  node -v
  npm -v
  ```

---

## 2. Instalar o Angular CLI
O Angular CLI (Command Line Interface) facilita a criação e o gerenciamento de projetos Angular.

- **Instale o Angular CLI globalmente:**
  ```bash
  npm install -g @angular/cli
  ```
- **Verifique a instalação:**
  ```bash
  ng version
  ```

---

## 3. Criar um Novo Projeto Angular

1. **Crie um novo projeto usando o Angular CLI:**
   ```bash
   ng new meu-projeto
   ```

   - Durante a criação, você será perguntado se deseja adicionar o **Angular routing** (roteamento) e qual estilo de folha de estilo (CSS, SCSS, etc.) prefere.

2. **Entre no diretório do projeto:**
   ```bash
   cd meu-projeto
   ```

3. **Inicie o servidor de desenvolvimento:**
   ```bash
   ng serve
   ```

   - O projeto estará disponível em `http://localhost:4200`.

---

## 4. Estrutura do Projeto Angular
Ao criar um projeto Angular, você verá uma estrutura básica com os seguintes diretórios importantes:

- **`src/app/`**: Contém os componentes principais do aplicativo.
- **`src/assets/`**: Armazena imagens e outros recursos estáticos.
- **`src/environments/`**: Arquivos de configuração para diferentes ambientes (desenvolvimento, produção).

---

## 5. Comandos Úteis do Angular CLI

- **Gerar um novo componente:**
  ```bash
  ng generate component nome-componente
  ```

- **Gerar um novo serviço:**
  ```bash
  ng generate service nome-servico
  ```

- **Criar um novo módulo:**
  ```bash
  ng generate module nome-modulo
  ```

- **Build para produção:**
  ```bash
  ng build --prod
  ```

- **Executar testes unitários:**
  ```bash
  ng test
  ```

- **Executar testes end-to-end:**
  ```bash
  ng e2e
  ```

---

## 6. Configuração de Controle de Versão

### Instale o Git: [Git Download](https://git-scm.com/)
### Configure um `.gitignore` automaticamente (já incluído pelo Angular CLI):

Exemplo de `.gitignore`:
```gitignore
node_modules/
dist/
*.env
```

---

## 7. Configurar ESLint para Angular
O Angular CLI usa o **TSLint** por padrão (em versões mais antigas), mas é recomendado migrar para o **ESLint**.

1. **Instale as dependências necessárias:**
   ```bash
   ng add @angular-eslint/schematics
   ```

2. **Converta a configuração do TSLint para ESLint:**
   ```bash
   ng g @angular-eslint/schematics:convert-tslint-to-eslint
   ```

3. **Adicione um script ao `package.json` para verificar o lint:**
   ```json
   "scripts": {
     "lint": "ng lint"
   }
   ```

4. **Execute o lint para verificar problemas no código:**
   ```bash
   npm run lint
   ```

---

## 8. Ferramentas Opcionais

### 1. **Instale o Prettier para Formatação de Código**

- **Instale as dependências:**
  ```bash
  npm install prettier eslint-config-prettier eslint-plugin-prettier --save-dev
  ```

- **Configure o Prettier no `.eslintrc.json`:**
  ```json
  {
    "extends": ["plugin:prettier/recommended"]
  }
  ```

- **Crie um arquivo `.prettierrc`:**
  ```json
  {
    "singleQuote": true,
    "semi": true
  }
  ```

### 2. **Configurar Husky e Lint-Staged**

- **Instale as dependências:**
  ```bash
  npm install husky lint-staged --save-dev
  ```

- **Adicione ao `package.json`:**
  ```json
  "husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  },
  "lint-staged": {
    "**/*.ts": ["eslint --fix", "prettier --write"]
  }
  ```

---

Com essas etapas e ferramentas, você terá um ambiente Angular pronto para desenvolvimento eficiente!
