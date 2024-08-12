# Generics

**Generics** em TypeScript são uma ferramenta poderosa que permite criar componentes flexíveis e reutilizáveis. Eles possibilitam que você defina funções, classes e interfaces que não estão vinculadas a um tipo específico, mas que funcionam com qualquer tipo de dado. Isso é especialmente útil quando você deseja escrever código que funcione de maneira uniforme para diferentes tipos de entrada.

## Introdução aos Generics

Um exemplo simples de generics é uma função que retorna o valor que recebe como argumento. Sem generics, você teria que definir essa função várias vezes para cada tipo:

**Sem Generics:**

```typescript
function retornaString(valor: string): string {
    return valor;
}

function retornaNumero(valor: number): number {
    return valor;
}
```

Com generics, você pode escrever uma única função que funciona para qualquer tipo:
**Com Generics:** 

```typescript
function retornaValor<T>(valor: T): T {
    return valor;
}
```
Aqui, `T` é um **parâmetro de tipo genérico** . Ele atua como um placeholder para o tipo que será usado quando a função for chamada.**Exemplo de Uso:** 

```typescript
let valorString = retornaValor<string>("Hello");
let valorNumero = retornaValor<number>(123);
```
No primeiro caso, `T` é substituído por `string`, e no segundo, por `number`. A função funciona de maneira segura para ambos os tipos.
## Generics em Funções 

Generics são frequentemente usados em funções que precisam trabalhar com diferentes tipos de entrada. Vamos considerar uma função que combina dois arrays em um único array:


```typescript
function combinarArrays<T>(array1: T[], array2: T[]): T[] {
    return array1.concat(array2);
}

let numeros = combinarArrays([1, 2, 3], [4, 5, 6]);
let strings = combinarArrays(["a", "b", "c"], ["d", "e", "f"]);
```

Nesta função:
 
- `T` representa qualquer tipo.
 
- `array1: T[]` e `array2: T[]` são arrays que contêm elementos do tipo `T`.
 
- O retorno é um novo array que contém elementos do tipo `T`.

Isso permite combinar arrays de números, strings ou qualquer outro tipo.

## Generics em Interfaces 

Você pode usar generics para criar interfaces que sejam flexíveis quanto aos tipos dos dados que manipulam. Isso é útil em cenários onde a estrutura dos dados é conhecida, mas o tipo exato pode variar.


```typescript
interface Par<T, U> {
    primeiro: T;
    segundo: U;
}

let parNumerico: Par<number, number> = { primeiro: 1, segundo: 2 };
let parMisto: Par<string, number> = { primeiro: "idade", segundo: 30 };
```
Aqui, a interface `Par` aceita dois tipos genéricos, `T` e `U`. Isso permite criar pares de diferentes tipos, como `number` e `string`.
## Generics em Classes 

Generics também são poderosos quando usados em classes. Eles permitem que uma classe opere sobre qualquer tipo especificado, aumentando a reutilização do código.


```typescript
class Caixa<T> {
    conteudo: T;

    constructor(conteudo: T) {
        this.conteudo = conteudo;
    }

    abrir(): T {
        return this.conteudo;
    }
}

let caixaDeString = new Caixa<string>("Um presente");
let caixaDeNumero = new Caixa<number>(123);

console.log(caixaDeString.abrir()); // Saída: "Um presente"
console.log(caixaDeNumero.abrir()); // Saída: 123
```
Neste exemplo, a classe `Caixa` pode armazenar qualquer tipo de dado e retorna o mesmo tipo ao chamar o método `abrir`.
## Restrições em Generics 
Às vezes, você pode querer que um tipo genérico seja limitado a um subconjunto específico de tipos. Isso é feito usando **constraints**  (restrições).

```typescript
function imprimirNome<T extends { nome: string }>(obj: T): void {
    console.log(obj.nome);
}

imprimirNome({ nome: "Nalberth" }); // Saída: "Nalberth"
// imprimirNome({ idade: 30 }); // Erro: Propriedade 'nome' está ausente no tipo '{ idade: number }'.
```
Aqui, `T` é restrito a tipos que têm uma propriedade `nome` do tipo `string`. Isso permite que o TypeScript verifique que o objeto passado possui uma propriedade `nome`, evitando erros.
## Conclusão 

Generics são uma ferramenta essencial para escrever código TypeScript flexível e reutilizável. Eles permitem que você crie funções, classes e interfaces que funcionam de maneira uniforme para diferentes tipos, melhorando a robustez e a versatilidade do seu código. Com o uso de generics, você pode garantir que suas abstrações sejam seguras e fáceis de manter.