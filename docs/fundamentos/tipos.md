# Tipos Básicos

Os tipos são a base da tipagem estática em TypeScript. Eles permitem que você defina quais tipos de dados são esperados em variáveis, parâmetros de função e valores de retorno, ajudando a prevenir erros comuns de programação.

## Tipos Primitivos

### 1. **Number**

O tipo `number` é usado para representar números, sejam eles inteiros ou de ponto flutuante.

**Exemplo:**

```typescript
let idade: number = 30;
let temperatura: number = 36.5;
```
Você pode usar `number` para representar idades, contagens, temperaturas, ou qualquer outro valor numérico.2. **String** O tipo `string` é usado para representar textos. Strings em TypeScript são delimitadas por aspas simples (`'`), aspas duplas (`"`), ou crases (`).**Exemplo:** 

```typescript
let nome: string = "Nalberth";
let saudacao: string = `Olá, ${nome}!`;
```

Strings são ideais para armazenar nomes, mensagens, ou qualquer outro tipo de texto.
3. **Boolean** O tipo `boolean` só pode ter dois valores: `true` ou `false`. Ele é usado em situações onde você precisa de uma condição binária, como para verificar se algo é verdadeiro ou falso.**Exemplo:** 

```typescript
let isAluno: boolean = true;
let aprovado: boolean = false;
```

Booleans são comumente usados em condicionais e loops.

## Tipos Complexos 
4. **Array** Arrays em TypeScript são usados para armazenar uma coleção de valores do mesmo tipo. Você pode definir um array usando `tipo[]` ou `Array<tipo>`.**Exemplo:** 

```typescript
let numeros: number[] = [1, 2, 3, 4, 5];
let nomes: Array<string> = ["Ana", "João", "Carlos"];
```

Arrays são úteis para armazenar listas de dados, como números ou strings.
5. **Tupla** 
Tuplas são arrays de tamanho fixo onde cada elemento pode ter um tipo diferente. Elas são úteis quando você sabe exatamente quantos elementos você terá e quais serão os tipos deles.
**Exemplo:** 

```typescript
let pessoa: [string, number] = ["Nalberth", 30];
```
Neste exemplo, a tupla `pessoa` armazena um nome e uma idade, garantindo que o primeiro elemento seja uma `string` e o segundo um `number`.6. **Enum** 
Enums permitem definir um conjunto de valores nomeados, que são mapeados para valores numéricos por padrão. Eles são úteis quando você tem um grupo fixo de valores relacionados.
**Exemplo:** 

```typescript
enum Cor {
    Vermelho,
    Verde,
    Azul
}

let minhaCor: Cor = Cor.Verde;
```

Enums facilitam a leitura do código ao substituir valores literais por nomes significativos.

## Inferência de Tipos 

TypeScript possui um sistema de inferência de tipos poderoso, que pode automaticamente deduzir o tipo de uma variável com base em seu valor inicial.
**Exemplo:** 

```typescript
let mensagem = "Olá, TypeScript!"; // Inferido como string
let numero = 42;                   // Inferido como number
```

Embora a inferência de tipos seja útil, é uma boa prática explicitar os tipos em partes críticas do código, especialmente em interfaces públicas (como parâmetros de função e valores de retorno).

## União de Tipos 

União de tipos permite que uma variável ou função aceite mais de um tipo. Isso é útil em casos onde o valor pode ser de diferentes tipos.
**Exemplo:** 

```typescript
let id: number | string;
id = 123;        // válido
id = "ABC123";   // também válido
```
Aqui, a variável `id` pode ser tanto um `number` quanto uma `string`.
## Conclusão 

Entender e utilizar os tipos corretamente em TypeScript é fundamental para aproveitar ao máximo a segurança oferecida pela tipagem estática. Ao especificar tipos, você cria código mais robusto e fácil de entender, reduzindo a probabilidade de erros.