# PI3-ES-2024-T22-FUN

## 📋 Sobre o Projeto

Este é um projeto Firebase desenvolvido para o curso de Engenharia de Software (PI3 - Projeto Integrador 3) pela equipe T22. O projeto utiliza Firebase Cloud Functions com TypeScript para implementar funcionalidades serverless.

## 🚀 Tecnologias Utilizadas

- **Firebase**: Plataforma de desenvolvimento de aplicativos
  - Cloud Functions
  - Firestore Database
  - Firebase Storage
  - Firebase Authentication
- **TypeScript**: Linguagem de programação
- **Node.js**: Ambiente de execução (v18)
- **ESLint**: Linter para garantir qualidade de código

## 📁 Estrutura do Projeto

```
PI3-ES-2024-T22-FUN/
├── functions/              # Diretório das Cloud Functions
│   ├── src/               # Código-fonte TypeScript
│   │   └── index.ts       # Ponto de entrada das functions
│   ├── lib/               # Código compilado (gerado)
│   ├── package.json       # Dependências e scripts
│   ├── tsconfig.json      # Configuração do TypeScript
│   └── .eslintrc.js       # Configuração do ESLint
├── firebase.json          # Configuração principal do Firebase
├── firestore.rules        # Regras de segurança do Firestore
├── firestore.indexes.json # Índices do Firestore
├── storage.rules          # Regras de segurança do Storage
├── .firebaserc            # Configuração do projeto Firebase
└── README.md              # Este arquivo
```

## 🔧 Pré-requisitos

Antes de começar, você precisa ter instalado em sua máquina:

- [Node.js](https://nodejs.org/) (versão 18 ou superior)
- [npm](https://www.npmjs.com/) (gerenciador de pacotes do Node.js)
- [Firebase CLI](https://firebase.google.com/docs/cli) (para deploy e emuladores)

### Instalando o Firebase CLI

```bash
npm install -g firebase-tools
```

## 📦 Instalação

1. Clone o repositório:
```bash
git clone https://github.com/JONTK123/PI3-ES-2024-T22-FUN.git
cd PI3-ES-2024-T22-FUN
```

2. Instale as dependências das Cloud Functions:
```bash
cd functions
npm install
```

## 🔑 Configuração do Firebase

1. Faça login no Firebase:
```bash
firebase login
```

2. O projeto está configurado para usar o projeto Firebase `puck-lock-446d0`. Se você precisar usar outro projeto:
```bash
firebase use --add
```

## 💻 Desenvolvimento

### Scripts Disponíveis

No diretório `functions/`, você pode executar:

- **`npm run lint`**: Executa o ESLint para verificar problemas no código
- **`npm run build`**: Compila o código TypeScript para JavaScript
- **`npm run build:watch`**: Compila o código em modo watch (recompila automaticamente)
- **`npm run serve`**: Inicia os emuladores do Firebase (apenas functions)
- **`npm run shell`**: Abre um shell interativo para testar as functions
- **`npm run start`**: Alias para `npm run shell`
- **`npm run deploy`**: Faz deploy das functions para o Firebase
- **`npm run logs`**: Visualiza os logs das functions em produção

### Usando os Emuladores do Firebase

Os emuladores permitem testar seu projeto localmente sem usar recursos do Firebase em produção.

1. Inicie todos os emuladores:
```bash
firebase emulators:start
```

2. Os seguintes serviços estarão disponíveis:
   - **Authentication**: http://localhost:9099
   - **Cloud Functions**: http://localhost:5001
   - **Firestore**: http://localhost:8080
   - **Storage**: http://localhost:9199
   - **Emulator UI**: http://localhost:4000 (interface web para gerenciar os emuladores)

### Desenvolvendo Cloud Functions

1. Abra o arquivo `functions/src/index.ts`
2. Escreva suas Cloud Functions seguindo a [documentação oficial](https://firebase.google.com/docs/functions)
3. Compile o código:
```bash
npm run build
```
4. Teste localmente usando os emuladores

Exemplo de uma função básica:

```typescript
import * as functions from "firebase-functions";

export const helloWorld = functions.https.onRequest((request, response) => {
  response.send("Hello from Firebase!");
});
```

## 🚢 Deploy

### Deploy das Cloud Functions

Para fazer deploy apenas das functions:
```bash
cd functions
npm run deploy
```

### Deploy Completo

Para fazer deploy de todo o projeto (functions, rules, indexes):
```bash
firebase deploy
```

### Deploy de Componentes Específicos

- **Apenas Firestore rules**: `firebase deploy --only firestore:rules`
- **Apenas Storage rules**: `firebase deploy --only storage`
- **Apenas Functions**: `firebase deploy --only functions`

## 🔒 Segurança

### Regras do Firestore

As regras de segurança do Firestore estão definidas em `firestore.rules`. Por padrão, todas as operações de leitura e escrita estão bloqueadas:

```javascript
allow read, write: if false;
```

⚠️ **IMPORTANTE**: Antes de usar o Firestore em produção, você deve configurar regras de segurança apropriadas!

### Regras do Storage

As regras de segurança do Storage estão em `storage.rules`. Da mesma forma, todas as operações estão bloqueadas por padrão.

## 🧪 Testes

Para adicionar testes às suas functions, você pode usar o `firebase-functions-test` que já está incluído nas dependências de desenvolvimento.

Exemplo básico:

```typescript
import * as test from "firebase-functions-test";
const testEnv = test();

// Seus testes aqui

testEnv.cleanup();
```

## 📝 Boas Práticas

1. **Sempre teste localmente** usando os emuladores antes de fazer deploy
2. **Use TypeScript** para aproveitar a tipagem estática e evitar erros
3. **Execute o linter** antes de commitar: `npm run lint`
4. **Compile o código** e verifique erros: `npm run build`
5. **Configure regras de segurança** adequadas antes de usar em produção
6. **Monitore os logs** após o deploy: `npm run logs`
7. **Mantenha as dependências atualizadas** e corrija vulnerabilidades de segurança

## 🐛 Troubleshooting

### Erro: "Unsupported engine"

Se você receber um aviso sobre a versão do Node.js, certifique-se de estar usando Node.js 18. Você pode usar [nvm](https://github.com/nvm-sh/nvm) para gerenciar versões:

```bash
nvm install 18
nvm use 18
```

### Erro ao iniciar emuladores

Se os emuladores não iniciarem, verifique se as portas não estão em uso:
- Auth: 9099
- Functions: 5001
- Firestore: 8080
- Storage: 9199

### Vulnerabilidades de segurança npm

Execute para corrigir vulnerabilidades:
```bash
npm audit fix
```

## 📚 Documentação Adicional

- [Documentação do Firebase](https://firebase.google.com/docs)
- [Cloud Functions para Firebase](https://firebase.google.com/docs/functions)
- [TypeScript](https://www.typescriptlang.org/docs/)
- [Firestore](https://firebase.google.com/docs/firestore)
- [Firebase CLI Reference](https://firebase.google.com/docs/cli)

## 👥 Equipe

**Projeto Integrador 3 - Engenharia de Software 2024**
- Equipe: T22
- Repositório: [JONTK123/PI3-ES-2024-T22-FUN](https://github.com/JONTK123/PI3-ES-2024-T22-FUN)

## 📄 Licença

Este é um projeto acadêmico desenvolvido para fins educacionais.

## 🤝 Contribuindo

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/MinhaFeature`)
3. Commit suas mudanças (`git commit -m 'Adiciona MinhaFeature'`)
4. Push para a branch (`git push origin feature/MinhaFeature`)
5. Abra um Pull Request

---

**Desenvolvido com ❤️ pela Equipe T22**
