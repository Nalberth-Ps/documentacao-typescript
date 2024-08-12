# Union Types

**Union Types** em TypeScript permitem que uma variável, parâmetro ou função aceite mais de um tipo de dado. Isso é especialmente útil quando você precisa de flexibilidade, mas ainda quer manter a segurança de tipos.

## Definindo Union Types

Para definir um union type, você usa o operador `|`, que representa "ou". Isso permite que uma variável possa ser de um tipo ou outro.

**Exemplo:**

```typescript
let id: number | string;

id = 123;       // válido
id = "ABC123";  // válido
// id = true;   // Erro: 'boolean' não é atribuível a 'number | string'
```
Neste exemplo, a variável `id` pode ser um número ou uma string, mas não pode ser um booleano.
## Usando Union Types em Funções 

Funções podem utilizar union types para aceitar diferentes tipos de parâmetros, mas você precisa lidar com cada caso dentro da função.
**Exemplo:** 

```typescript
function imprimirId(id: number | string): void {
    if (typeof id === "number") {
        console.log(`ID numérico: ${id}`);
    } else {
        console.log(`ID string: ${id}`);
    }
}

imprimirId(123);       // Saída: "ID numérico: 123"
imprimirId("ABC123");  // Saída: "ID string: ABC123"
```
Neste exemplo, a função `imprimirId` aceita um número ou uma string e lida com cada caso separadamente.
## Union Types em Arrays 

Você também pode usar union types em arrays, permitindo que o array contenha elementos de diferentes tipos.
**Exemplo:** 

```typescript
let valores: (number | string)[] = [1, "dois", 3, "quatro"];

valores.push(5);      // válido
valores.push("seis"); // válido
// valores.push(true); // Erro: 'boolean' não é atribuível a 'number | string'
```
Neste caso, `valores` é um array que pode conter números e strings, mas não outros tipos.
## Conclusão 

Union types fornecem flexibilidade em situações onde uma variável ou função precisa trabalhar com múltiplos tipos. No entanto, é importante usá-los com cuidado para evitar complexidade excessiva no código. Eles são mais adequados para cenários onde a flexibilidade é necessária, mas a clareza e segurança de tipos ainda são prioridades.