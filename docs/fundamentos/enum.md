# Enum

**Enums** (abreviação de "enumerations") permitem a definição de um conjunto de valores nomeados que podem ser usados como constantes, proporcionando maior legibilidade e segurança ao código. Em TypeScript, os `enums` podem ser tanto numéricos quanto baseados em strings.

## Enums Numéricos

Os `enums` numéricos são o tipo mais comum. Cada valor no enum é associado a um número, começando do zero por padrão, mas você pode alterar essa numeração.

**Exemplo:**

```typescript
enum Cor {
    Vermelho, // 0
    Verde,    // 1
    Azul      // 2
}

let corFavorita: Cor = Cor.Verde;
console.log(corFavorita); // Saída: 1
```

Você pode personalizar o valor inicial, e os valores subsequentes serão incrementados automaticamente.
**Exemplo com Valores Personalizados:** 

```typescript
enum Cor {
    Vermelho = 1,
    Verde,    // 2
    Azul      // 3
}
```

## Enums Baseados em Strings 
Os `enums` baseados em strings associam cada valor do enum a uma string. Eles são úteis quando você quer que os valores do enum sejam mais legíveis ou quando precisa trabalhar com strings em vez de números.**Exemplo:** 

```typescript
enum Status {
    Sucesso = "SUCESSO",
    Erro = "ERRO",
    Carregando = "CARREGANDO"
}

let estadoAtual: Status = Status.Carregando;
console.log(estadoAtual); // Saída: "CARREGANDO"
```
Os `enums` baseados em strings não são incrementados automaticamente e exigem que você defina explicitamente os valores para cada membro.
## Usando Enums em Funções 
Os `enums` podem ser usados em funções para restringir os parâmetros a um conjunto específico de valores, tornando a função mais segura e fácil de entender.**Exemplo:** 

```typescript
function responder(status: Status): void {
    if (status === Status.Sucesso) {
        console.log("Operação realizada com sucesso!");
    } else if (status === Status.Erro) {
        console.log("Ocorreu um erro na operação.");
    }
}

responder(Status.Sucesso); // Saída: "Operação realizada com sucesso!"
```

## Conclusão 

Enums são uma maneira poderosa de trabalhar com conjuntos fixos de valores. Eles melhoram a legibilidade do código e ajudam a evitar erros comuns, como o uso de valores mágicos. Ao entender como e quando usar enums, você pode tornar seu código TypeScript mais expressivo e seguro.