# Funções

As funções são blocos fundamentais de código que permitem agrupar e reutilizar lógica. Em TypeScript, as funções podem ser tipadas para garantir que os valores corretos sejam passados e retornados, o que ajuda a prevenir erros comuns e torna o código mais robusto.

## Declaração de Funções

A declaração de funções em TypeScript é semelhante ao JavaScript, mas com a adição de tipos para parâmetros e valores de retorno.

**Exemplo:**

```typescript
function soma(a: number, b: number): number {
    return a + b;
}
```
 
- **`a: number`**  e ****`a: number`**  e `b: number`**  especificam que ambos os parâmetros devem ser números.
 
- **`: number`**  após os parênteses indica que a função retorna um número.
Se você tentar passar um valor que não seja um número para a função `soma`, TypeScript gerará um erro:

```typescript
// soma(10, "20"); // Erro: Argumento de tipo 'string' não é atribuível ao parâmetro de tipo 'number'.
```

## Funções Anônimas 

As funções anônimas, ou funções expressas, são funções sem nome que são geralmente atribuídas a variáveis. Em TypeScript, elas também podem ser tipadas.
**Exemplo:** 

```typescript
let somar = function(a: number, b: number): number {
    return a + b;
};
```

Funções anônimas são úteis quando você precisa passar uma função como argumento ou usá-la como um retorno de outra função.

## Parâmetros Opcionais e Valores Padrão 
Em TypeScript, você pode definir parâmetros opcionais usando o símbolo `?` e fornecer valores padrão para parâmetros, o que é útil para evitar a necessidade de verificar se um parâmetro foi passado.**Parâmetros Opcionais:** 

```typescript
function saudar(nome: string, saudacao?: string): string {
    return saudacao ? `${saudacao}, ${nome}!` : `Olá, ${nome}!`;
}

console.log(saudar("Nalberth"));            // Saída: "Olá, Nalberth!"
console.log(saudar("Nalberth", "Bom dia")); // Saída: "Bom dia, Nalberth!"
```
 
- O parâmetro `saudacao` é opcional. Se não for fornecido, a função usa um valor padrão.
**Valores Padrão:** 

```typescript
function saudarComDefault(nome: string, saudacao: string = "Olá"): string {
    return `${saudacao}, ${nome}!`;
}

console.log(saudarComDefault("Nalberth"));            // Saída: "Olá, Nalberth!"
console.log(saudarComDefault("Nalberth", "Bom dia")); // Saída: "Bom dia, Nalberth!"
```
 
- Neste exemplo, `saudacao` tem um valor padrão de `"Olá"`, que é usado se nenhum valor for passado.

## Funções Assíncronas (async/await) 
O TypeScript suporta funções assíncronas usando `async` e `await`, que facilitam o trabalho com operações assíncronas, como chamadas de API.**Exemplo:** 

```typescript
async function fetchData(url: string): Promise<any> {
    const response = await fetch(url);
    return response.json();
}

fetchData("https://api.exemplo.com/dados")
    .then(data => console.log(data))
    .catch(error => console.error(error));
```
 
- A palavra-chave `async` faz com que a função retorne uma `Promise`.
 
- O `await` pausa a execução da função até que a `Promise` seja resolvida.

## Funções com Sobrecarga (Overloading) 

O TypeScript permite definir várias assinaturas para uma função, permitindo que ela aceite diferentes tipos de argumentos e retorne diferentes tipos de resultados.
**Exemplo:** 

```typescript
function combinar(a: string, b: string): string;
function combinar(a: number, b: number): number;
function combinar(a: any, b: any): any {
    if (typeof a === "string" && typeof b === "string") {
        return a + b;
    } else if (typeof a === "number" && typeof b === "number") {
        return a + b;
    }
}

console.log(combinar("Olá, ", "Mundo!")); // Saída: "Olá, Mundo!"
console.log(combinar(10, 20));            // Saída: 30
```
 
- A função `combinar` pode aceitar tanto strings quanto números, mas cada tipo tem um comportamento específico.

## Conclusão 

As funções em TypeScript são ferramentas poderosas que permitem criar código limpo e eficiente. Com a tipagem estática, você pode prevenir muitos erros comuns e garantir que suas funções sejam usadas corretamente. Entender como tipar parâmetros, valores de retorno, e como trabalhar com recursos como async/await e sobrecarga de funções é essencial para escrever código TypeScript robusto.