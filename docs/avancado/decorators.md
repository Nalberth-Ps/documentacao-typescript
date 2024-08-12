# Decorators

**Decorators** em TypeScript são uma forma especial de declarar metadados e adicionar comportamentos a classes, métodos, propriedades ou parâmetros. Eles permitem modificar ou estender o comportamento de uma classe ou membro da classe de maneira declarativa, facilitando a reutilização de código e a implementação de padrões de design como o decorator pattern.

## Introdução aos Decorators

Decorators são funções que são aplicadas a classes, métodos, acessores, propriedades ou parâmetros no momento da definição. Eles são prefixados com `@` e podem ser aplicados diretamente sobre as declarações.

**Exemplo de um Decorator Simples:**

```typescript
function logClass(constructor: Function) {
    console.log(`Classe decorada: ${constructor.name}`);
}

@logClass
class Pessoa {
    nome: string;

    constructor(nome: string) {
        this.nome = nome;
    }
}
```
Neste exemplo, o decorator `logClass` é aplicado à classe `Pessoa`. Quando a classe é definida, o decorator é executado, registrando o nome da classe no console.
## Tipos de Decorators 
1. **Class Decorators** 
Class decorators são aplicados à declaração de uma classe e recebem o construtor da classe como argumento. Eles podem modificar ou substituir a classe original.
**Exemplo:** 

```typescript
function seloDeClasse<T extends { new(...args: any[]): {} }>(constructor: T) {
    return class extends constructor {
        selo = "Classe Decorada";
    };
}

@seloDeClasse
class Produto {
    nome: string;

    constructor(nome: string) {
        this.nome = nome;
    }
}

let produto = new Produto("Livro");
console.log(produto.selo); // Saída: "Classe Decorada"
```
Aqui, o decorator `seloDeClasse` adiciona uma nova propriedade `selo` a todas as instâncias da classe `Produto`.2. **Method Decorators** 
Method decorators são aplicados a métodos de instâncias ou estáticos, permitindo que você modifique ou estenda o comportamento do método.
**Exemplo:** 

```typescript
function logarMetodo(target: any, propertyName: string, descriptor: PropertyDescriptor) {
    const metodoOriginal = descriptor.value;

    descriptor.value = function(...args: any[]) {
        console.log(`Método ${propertyName} chamado com argumentos:`, args);
        return metodoOriginal.apply(this, args);
    };
}

class Calculadora {
    @logarMetodo
    somar(a: number, b: number): number {
        return a + b;
    }
}

const calc = new Calculadora();
calc.somar(2, 3); // Saída: "Método somar chamado com argumentos: [2, 3]"
```
O decorator `logarMetodo` intercepta a chamada ao método `somar` e registra os argumentos antes de executar o método original.3. **Accessor Decorators** 
Accessor decorators são aplicados a acessores (getters e setters) de propriedades, permitindo modificar como a propriedade é acessada ou modificada.
**Exemplo:** 

```typescript
function bloquearAccessor(target: any, propertyName: string, descriptor: PropertyDescriptor) {
    descriptor.set = function(value: any) {
        console.log(`Tentativa de alterar ${propertyName} bloqueada.`);
    };
}

class Conta {
    private _saldo: number = 0;

    @bloquearAccessor
    set saldo(valor: number) {
        this._saldo = valor;
    }

    get saldo(): number {
        return this._saldo;
    }
}

let conta = new Conta();
conta.saldo = 100; // Saída: "Tentativa de alterar saldo bloqueada."
console.log(conta.saldo); // Saída: 0
```
O decorator `bloquearAccessor` bloqueia a modificação da propriedade `saldo`, evitando que o valor seja alterado.4. **Property Decorators** 
Property decorators são aplicados a propriedades de instâncias. Eles podem ser usados para alterar a definição de uma propriedade ou para adicionar metadados.
**Exemplo:** 

```typescript
function somenteLeitura(target: any, propertyName: string) {
    const descriptor: PropertyDescriptor = {
        writable: false
    };
    Object.defineProperty(target, propertyName, descriptor);
}

class Usuario {
    @somenteLeitura
    nome: string;

    constructor(nome: string) {
        this.nome = nome;
    }
}

let usuario = new Usuario("Nalberth");
usuario.nome = "Outro Nome"; // Erro: Não é possível atribuir a 'nome' porque é uma propriedade somente leitura.
```
O decorator `somenteLeitura` marca a propriedade `nome` como `readonly`, impedindo que seu valor seja alterado após a inicialização.5. **Parameter Decorators** 
Parameter decorators são usados para adicionar metadados a parâmetros de métodos, mas diferentemente dos outros tipos de decorators, eles não podem alterar o comportamento do método.
**Exemplo:** 

```typescript
function logarParametro(target: any, propertyName: string, parameterIndex: number) {
    console.log(`O parâmetro no índice ${parameterIndex} do método ${propertyName} foi decorado.`);
}

class Servico {
    metodo(@logarParametro mensagem: string) {
        console.log(mensagem);
    }
}

let servico = new Servico();
servico.metodo("Olá, Decorators!");
```
Neste exemplo, `logarParametro` registra o índice e o nome do método em que o decorator foi aplicado.
## Conclusão 

Decorators são uma característica avançada e poderosa do TypeScript que permitem adicionar comportamentos a classes e seus membros de maneira declarativa e reutilizável. Eles são amplamente utilizados em frameworks como Angular para injeção de dependência e outros padrões. Entender como e quando usar decorators pode levar sua habilidade de programação a um novo nível, permitindo a criação de código mais modular e expressivo.