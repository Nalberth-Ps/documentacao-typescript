# TypeScript com Node.js

TypeScript é uma ferramenta poderosa para o desenvolvimento com Node.js, trazendo tipagem estática, interfaces, e muitas outras funcionalidades que facilitam a manutenção e escalabilidade de projetos. Vamos explorar como configurar e utilizar TypeScript em um ambiente Node.js.

## Configurando um Projeto Node.js com TypeScript

Para começar, crie um novo diretório para o seu projeto e inicialize o npm:

```bash
mkdir meu-projeto-node
cd meu-projeto-node
npm init -y
```

Em seguida, instale TypeScript e as definições de tipo para Node.js:


```bash
npm install typescript @types/node --save-dev
```
Agora, inicialize o TypeScript criando o arquivo de configuração `tsconfig.json`:

```bash
npx tsc --init
```
Esse comando cria um arquivo `tsconfig.json` básico. Aqui está uma configuração comum para projetos Node.js:

```json
{
  "compilerOptions": {
    "target": "ES6",
    "module": "commonjs",
    "strict": true,
    "esModuleInterop": true,
    "outDir": "./dist",
    "rootDir": "./src"
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules"]
}
```
Essa configuração define que o TypeScript irá compilar o código para ES6 e usará o sistema de módulos `commonjs`.
## Criando um Servidor HTTP com TypeScript 

Vamos criar um simples servidor HTTP usando TypeScript:

1. Crie a estrutura de pastas:


```bash
mkdir src
touch src/server.ts
```
 
1. Adicione o seguinte código ao arquivo `src/server.ts`:


```typescript
import * as http from 'http';

const server = http.createServer((req, res) => {
    res.statusCode = 200;
    res.setHeader('Content-Type', 'text/plain');
    res.end('Hello, TypeScript with Node.js!\n');
});

const PORT = 3000;
server.listen(PORT, () => {
    console.log(`Servidor rodando em http://localhost:${PORT}/`);
});
```

1. Para compilar e executar o servidor:


```bash
npx tsc
node dist/server.js
```

Este código cria um servidor HTTP simples que responde com uma mensagem de texto.

## Uso de Modulos em TypeScript 
Em TypeScript, você pode organizar seu código em módulos, que são compilados para o formato `commonjs` ou `ES6`, dependendo da sua configuração.**Exemplo:** 

```typescript
// src/mathUtils.ts
export function somar(a: number, b: number): number {
    return a + b;
}
```


```typescript
// src/server.ts
import { somar } from './mathUtils';

const resultado = somar(10, 20);
console.log(`Resultado da soma: ${resultado}`);
```
Nesse exemplo, o módulo `mathUtils` exporta uma função `somar`, que é importada e usada em `server.ts`.
## Integrando Ferramentas de Build 
Em projetos Node.js, você pode integrar TypeScript com ferramentas de build como `ts-node` para executar código TypeScript diretamente sem a necessidade de compilação prévia.

```bash
npm install ts-node --save-dev
```

Agora você pode executar seu servidor diretamente:


```bash
npx ts-node src/server.ts
```

Isso elimina a necessidade de compilar manualmente o código antes de executá-lo, o que é útil durante o desenvolvimento.

## Conclusão 

TypeScript traz muitos benefícios para o desenvolvimento com Node.js, incluindo tipagem estática, autocompletar aprimorado, e a detecção precoce de erros. Ele facilita a manutenção de projetos maiores e torna o código mais robusto e confiável. Integrar TypeScript em seu ambiente Node.js é uma escolha excelente para quem busca melhorar a qualidade e a escalabilidade de suas aplicações.