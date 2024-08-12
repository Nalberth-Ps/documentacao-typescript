# Introdução ao TypeScript

## O que é TypeScript?

TypeScript é um superconjunto tipado de JavaScript que compila para JavaScript puro. Ele adiciona tipagem estática e outros recursos, como interfaces e enumerações, que ajudam a prevenir erros comuns em tempo de desenvolvimento.

## Por que usar TypeScript?

### 1. **Segurança de Tipos**

Em JavaScript, você pode facilmente cometer erros de tipo que só serão descobertos em tempo de execução. Por exemplo:

```javascript
function soma(a, b) {
    return a + b;
}

console.log(soma(5, "10")); // Resultado: "510" (string)
```

Em TypeScript, você pode evitar esse tipo de erro especificando os tipos de entrada:


```typescript
function soma(a: number, b: number): number {
    return a + b;
}

// console.log(soma(5, "10")); // Erro: Argumento de tipo 'string' não é atribuível ao parâmetro de tipo 'number'.
```
2. **Melhor Autocompletar e Refatoração** 
TypeScript melhora significativamente a experiência do desenvolvedor ao trabalhar com editores de código, oferecendo autocompletar inteligente e verificação de tipos. Isso é especialmente útil em grandes bases de código.
**Exemplo Prático:** 
Com JavaScript:


```javascript
let usuario = { nome: "Nalberth", idade: 30 };
console.log(usuario.nome);
```

Se você errar o nome da propriedade, o erro só aparecerá em tempo de execução:


```javascript
console.log(usuario.nomes); // undefined
```

Com TypeScript:


```typescript
interface Usuario {
    nome: string;
    idade: number;
}

let usuario: Usuario = { nome: "Nalberth", idade: 30 };
console.log(usuario.nome);

// console.log(usuario.nomes); // Erro: A propriedade 'nomes' não existe no tipo 'Usuario'.
```
3. **Detecção Precoce de Erros** 
TypeScript permite que você identifique erros antes mesmo de executar o código, economizando tempo e evitando bugs em produção.
**Exemplo Prático:** 
Em JavaScript, você pode acidentalmente passar um número onde se espera uma string:


```javascript
function boasVindas(nome) {
    return "Bem-vindo, " + nome;
}

boasVindas(123); // "Bem-vindo, 123"
```

Em TypeScript, isso geraria um erro de compilação, evitando comportamentos inesperados:


```typescript
function boasVindas(nome: string): string {
    return "Bem-vindo, " + nome;
}

// boasVindas(123); // Erro: Argumento de tipo 'number' não é atribuível ao parâmetro de tipo 'string'.
```
4. **Melhor Suporte para Ferramentas de Build e Integração** 
TypeScript se integra bem com diversas ferramentas de build modernas, como Webpack e Babel, facilitando a configuração e o gerenciamento de projetos complexos.
**Exemplo Prático:** 
Usando TypeScript com React permite detectar erros de tipo em componentes, melhorando a confiabilidade da aplicação:


```typescript
interface Props {
    nome: string;
}

const BoasVindas: React.FC<Props> = ({ nome }) => {
    return <h1>Bem-vindo, {nome}!</h1>;
};

// <BoasVindas nome={123} /> // Erro: 'number' não é atribuível a 'string'.
```

## Instalação e Configuração 

Você pode instalar o TypeScript globalmente usando npm:


```bash
npm install -g typescript
```
Para começar um novo projeto TypeScript, crie um arquivo `tsconfig.json` que configurará o compilador:

```json
{
  "compilerOptions": {
    "target": "es5",
    "module": "commonjs",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true
  }
}
```

Isso configura o TypeScript para compilar o código em um formato compatível com a maioria dos navegadores e ambientes de execução, enquanto aplica regras rigorosas de tipagem.