# Readonly e Const

**Readonly** e **Const** são duas maneiras de garantir a imutabilidade no TypeScript, impedindo que variáveis ou propriedades sejam alteradas após a inicialização. Usá-los corretamente pode prevenir muitos erros de programação e melhorar a segurança do código.

## Readonly

A palavra-chave `readonly` pode ser aplicada a propriedades de classes e interfaces para garantir que essas propriedades não sejam modificadas após serem atribuídas.

**Exemplo:**

```typescript
class Usuario {
    readonly id: number;
    nome: string;

    constructor(id: number, nome: string) {
        this.id = id;
        this.nome = nome;
    }
}

let usuario = new Usuario(1, "Nalberth");
// usuario.id = 2; // Erro: 'id' é somente leitura e não pode ser alterado
```
No exemplo acima, a propriedade `id` é marcada como `readonly`, o que significa que ela só pode ser atribuída uma vez, normalmente no construtor.
### Readonly em Interfaces 
Você também pode usar `readonly` em interfaces para garantir que certas propriedades sejam imutáveis.**Exemplo:** 

```typescript
interface Produto {
    readonly codigo: number;
    nome: string;
}

let produto: Produto = { codigo: 123, nome: "Caneta" };
// produto.codigo = 456; // Erro: 'codigo' é somente leitura
```
Nesse caso, a propriedade `codigo` do objeto `Produto` não pode ser modificada depois de atribuída.
## Const 
A palavra-chave `const` é usada para declarar variáveis cujos valores não podem ser reatribuídos após a inicialização. É especialmente útil para valores que não devem mudar durante a execução do programa.**Exemplo:** 

```typescript
const PI = 3.14;
// PI = 3.1415; // Erro: Não é possível atribuir a 'PI' porque é uma constante
```
A constante `PI` não pode ser alterada depois de definida. O uso de `const` ajuda a garantir que valores críticos não sejam acidentalmente modificados.
### Const em Arrays e Objetos 
Embora `const` previna a reatribuição de variáveis, ele não impede a modificação dos conteúdos de arrays ou objetos.**Exemplo:** 

```typescript
const numeros = [1, 2, 3];
numeros.push(4); // válido, mas cuidado com modificações

const usuario = { nome: "Nalberth" };
usuario.nome = "Carlos"; // válido, mas o objeto `usuario` ainda é o mesmo
```
Mesmo com `const`, você pode alterar o conteúdo dos arrays e objetos. Para garantir imutabilidade completa, combine `const` com `readonly` ou técnicas de programação imutável.
## Conclusão 
O uso de `readonly` e `const` é fundamental para promover a imutabilidade no código TypeScript, reduzindo a probabilidade de bugs e melhorando a segurança do código. Incorporar essas práticas no seu desenvolvimento diário leva a um código mais previsível e confiável.