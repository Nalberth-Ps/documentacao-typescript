# Práticas Recomendadas em TypeScript

TypeScript é uma ferramenta poderosa que, quando usada corretamente, pode melhorar significativamente a qualidade do código. Esta seção cobre as práticas recomendadas para escrever código TypeScript robusto, claro e sustentável, garantindo que você aproveite ao máximo as capacidades da linguagem.

## 1. **Use Tipos Estritos**

Uma das maiores vantagens do TypeScript é a tipagem estática, que ajuda a evitar erros de tipo em tempo de execução. Ative as opções de tipagem estrita (`strict`) no `tsconfig.json` para garantir que o compilador aplique as regras mais rigorosas.

**Exemplo de Configuração:**

```json
{
  "compilerOptions": {
    "strict": true,
    "noImplicitAny": true,
    "strictNullChecks": true,
    "strictFunctionTypes": true,
    "strictBindCallApply": true,
    "alwaysStrict": true,
    "strictPropertyInitialization": true
  }
}
```

Essas opções forçam você a ser explícito sobre os tipos e reduzem a probabilidade de erros.
2. **Prefira Interfaces para Objetos** 
Embora o TypeScript permita a criação de tipos e interfaces para definir a forma de objetos, geralmente é preferível usar interfaces, pois elas são mais flexíveis e extensíveis.
**Exemplo:** 

```typescript
interface Usuario {
    nome: string;
    idade: number;
    email?: string; // Propriedade opcional
}

const usuario: Usuario = {
    nome: "Nalberth",
    idade: 30
};
```

Interfaces são mais adequadas para modelar dados complexos e permitem a extensão com facilidade.
3. Evite o Tipo `any`** O tipo `any` desabilita a verificação de tipo para uma variável, o que vai contra o propósito de usar TypeScript. Sempre que possível, evite `any` e opte por tipos mais específicos ou use união de tipos.**Exemplo Problemático:** 

```typescript
let dados: any;
dados = 123;
dados = "Texto";
dados = true; // Compila, mas perde a segurança de tipo
```
**Solução:** 

```typescript
let dados: number | string | boolean;
dados = 123;
dados = "Texto";
dados = true; // Agora, o tipo é restrito a `number`, `string` ou `boolean`
```
4. **Mantenha o Código Organizado com Módulos** 
Organize seu código em módulos e namespaces para melhorar a modularidade e facilitar a manutenção. Utilize o sistema de módulos do ES6 ou CommonJS, dependendo do ambiente de execução.
**Exemplo de Módulos:** 

```typescript
// mathUtils.ts
export function somar(a: number, b: number): number {
    return a + b;
}

// app.ts
import { somar } from './mathUtils';

console.log(somar(10, 20));
```

Isso mantém o código organizado e facilita a reutilização de funções em diferentes partes do projeto.
5. **Utilize Enum para Conjuntos de Valores Finitos** Quando você tem um conjunto fixo de valores que uma variável pode assumir, use `enum` para aumentar a legibilidade e a segurança.**Exemplo:** 

```typescript
enum Cor {
    Vermelho,
    Verde,
    Azul
}

let corFavorita: Cor = Cor.Verde;
```

Enums são particularmente úteis para representar estados, cores, opções de configuração, e outras coleções de valores fixos.
6. **Documente Seu Código com JSDoc** 
Mesmo com a tipagem estática, é importante documentar suas funções, classes e interfaces. O JSDoc é suportado pelo TypeScript e melhora a autocompletar, além de servir como uma referência rápida para outros desenvolvedores.
**Exemplo:** 

```typescript
/**
 * Soma dois números.
 * @param a - O primeiro número.
 * @param b - O segundo número.
 * @returns A soma de `a` e `b`.
 */
function somar(a: number, b: number): number {
    return a + b;
}
```

Essa documentação ajuda a entender rapidamente o propósito e o uso de uma função ou classe.
7. Utilize `readonly` e `const` Quando Possível** Utilize `readonly` para propriedades de classes que não devem ser alteradas após a inicialização, e `const` para variáveis que não devem ser reatribuídas.**Exemplo:** 

```typescript
class Usuario {
    readonly id: number;
    nome: string;

    constructor(id: number, nome: string) {
        this.id = id;
        this.nome = nome;
    }
}

const usuario: Usuario = new Usuario(1, "Nalberth");
// usuario.id = 2; // Erro: id é somente leitura
```

Isso protege contra modificações acidentais e torna a intenção do código mais clara.
8. **Evite Excessos de Union Types** Embora `union types` sejam úteis, evitá-los em excesso pode tornar o código difícil de entender e manter. Se você perceber que está usando muitos `union types`, considere reavaliar o design do código.**Exemplo:** 

```typescript
type Id = string | number | null | undefined;
```

Esse tipo de definição pode indicar que o design pode ser simplificado ou que uma abordagem diferente (como interfaces mais restritas) seria mais adequada.
9. **Prefira Funções Puramente Tipadas** Esforce-se para que suas funções sejam puramente tipadas, evitando `any`, e que retornem tipos claros e previsíveis. Isso melhora a previsibilidade e a segurança do código.**Exemplo:** 

```typescript
function processarDados(dados: string[]): string[] {
    return dados.map(dado => dado.toUpperCase());
}
```

Aqui, a função recebe um array de strings e retorna um array de strings, sem ambiguidade nos tipos.
10. **Testes com Tipagem Rigorosa** 
Ao escrever testes, utilize tipos rigorosos para garantir que os testes também estejam corretos e que as suposições sobre os tipos de dados sejam verificadas.
**Exemplo com Jest:** 

```typescript
test('deve somar dois números', () => {
    const resultado: number = somar(2, 3);
    expect(resultado).toBe(5);
});
```

Essa prática assegura que até mesmo os testes sejam mantidos dentro das boas práticas de tipagem.

## Conclusão 

Seguir essas práticas recomendadas ajudará você a tirar o máximo proveito do TypeScript, garantindo que seu código seja mais seguro, legível e fácil de manter. À medida que você adota essas práticas, verá uma melhora na qualidade geral de seus projetos TypeScript e na confiança com que desenvolve novas funcionalidades.