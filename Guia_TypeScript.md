# Guia de Configuração para Trabalhar com TypeScript

## 1. Instalar Node.js e npm
O Node.js vem com o npm (Node Package Manager), que é essencial para instalar TypeScript e outras dependências.

- **Baixe e instale o Node.js:** [Node.js Download](https://nodejs.org/)
- **Verifique a instalação:**
  ```bash
  node -v
  npm -v
  ```

---

## 2. Instalar o TypeScript
- **Use o npm para instalar o TypeScript globalmente:**
  ```bash
  npm install -g typescript
  ```
- **Verifique a instalação:**
  ```bash
  tsc -v
  ```

---

## 5. Configurar um Projeto TypeScript

### 1. Inicie um novo projeto Node.js:
```bash
mkdir meu-projeto
cd meu-projeto
npm init -y
```

### 2. Instale o TypeScript localmente no projeto (opcional, mas recomendado):
```bash
npm install typescript --save-dev
```

### 3. Gere um arquivo de configuração do TypeScript:
```bash
tsc --init
```
Isso criará um arquivo `tsconfig.json`. Edite conforme necessário. Exemplo básico:
```json
{
  "compilerOptions": {
    "target": "ES6",
    "module": "CommonJS",
    "strict": true,
    "outDir": "./dist",
    "rootDir": "./src"
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules"]
}
```

### 4. Estrutura do projeto:
- Crie um diretório `src` para armazenar os arquivos TypeScript:
  ```bash
  mkdir src
  touch src/index.ts
  ```

### 5. Compile o TypeScript:
- Para compilar o código manualmente:
  ```bash
  tsc
  ```
- Ou adicione um script no `package.json`:
  ```json
  "scripts": {
    "build": "tsc"
  }
  ```
  E execute:
  ```bash
  npm run build
  ```

---

## 6. Instalar Outras Dependências Úteis

### 1. **ts-node:** Para executar arquivos TypeScript diretamente (sem compilar):
```bash
npm install ts-node --save-dev
```
Execute o código:
```bash
npx ts-node src/index.ts
```

### 2. **nodemon:** Para reiniciar o servidor automaticamente ao salvar alterações:
```bash
npm install nodemon --save-dev
```
Adicione um script no `package.json`:
```json
"scripts": {
  "dev": "nodemon --watch src --exec ts-node src/index.ts"
}
```
Execute:
```bash
npm run dev
```

### 3. **ESLint:** Para linting:
```bash
npm install eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin --save-dev
```
Crie um arquivo `.eslintrc.json`:
```json
{
  "parser": "@typescript-eslint/parser",
  "plugins": ["@typescript-eslint"],
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/recommended"
  ]
}
```

---

## 7. Configurar Git e Controle de Versão

### Instale o Git: [Git Download](https://git-scm.com/)
### Configure um `.gitignore` no seu projeto:
```gitignore
node_modules/
dist/
*.env
```

---

## 8. Ferramentas Opcionais para Melhorar o Fluxo

### 1. **Prettier:** Para formatação consistente:
```bash
npm install prettier --save-dev
```
Crie um arquivo `.prettierrc`:
```json
{
  "semi": true,
  "singleQuote": true,
  "trailingComma": "all"
}
```

### 2. **Husky e Lint-Staged:** Para executar lint e testes antes de commits:
```bash
npm install husky lint-staged --save-dev
```
Adicione ao `package.json`:
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

Com essas ferramentas e configurações, você estará pronto para trabalhar eficientemente com TypeScript!
