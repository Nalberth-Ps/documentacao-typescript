# Classes

Em TypeScript, uma classe é uma estrutura que permite criar objetos com propriedades e métodos associados. As classes encapsulam dados e comportamentos que são comuns a todas as instâncias da classe. Vamos explorar como definir classes, aplicar herança, e utilizar modificadores de acesso para controlar a visibilidade dos membros da classe.

## Definindo Classes

Uma classe em TypeScript é definida usando a palavra-chave `class`, seguida pelo nome da classe. Dentro da classe, podemos definir propriedades e métodos. O método `constructor` é especial e é chamado automaticamente quando um novo objeto da classe é criado.

```typescript
class Pessoa {
    nome: string;
    idade: number;

    constructor(nome: string, idade: number) {
        this.nome = nome;
        this.idade = idade;
    }

    saudacao(): string {
        return `Olá, meu nome é ${this.nome} e eu tenho ${this.idade} anos.`;
    }
}
```
No exemplo acima, a classe `Pessoa` possui duas propriedades (`nome` e `idade`) e um método (`saudacao`). O método `constructor` inicializa as propriedades da classe quando um novo objeto é criado.
## Herança 

Herança é um conceito fundamental na POO, que permite que uma classe (subclasse) herde as propriedades e métodos de outra classe (superclasse). Isso facilita o reaproveitamento de código e a criação de estruturas hierárquicas.


```typescript
class Estudante extends Pessoa {
    curso: string;

    constructor(nome: string, idade: number, curso: string) {
        super(nome, idade);
        this.curso = curso;
    }

    saudacao(): string {
        return `${super.saudacao()} Estou estudando ${this.curso}.`;
    }
}
```
No exemplo acima, `Estudante` é uma subclasse de `Pessoa`. A palavra-chave `extends` é usada para indicar que `Estudante` herda de `Pessoa`. O método `saudacao` da subclasse `Estudante` chama o método `saudacao` da superclasse `Pessoa` usando `super()` e adiciona mais informações.
## Modificadores de Acesso 

Os modificadores de acesso em TypeScript controlam a visibilidade das propriedades e métodos de uma classe. Existem três modificadores principais:
 
- **public** : Acessível de qualquer lugar.
 
- **private** : Acessível apenas dentro da própria classe.
 
- **protected** : Acessível dentro da classe e em subclasses.


```typescript
class ContaBancaria {
    private saldo: number;

    constructor(saldoInicial: number) {
        this.saldo = saldoInicial;
    }

    public depositar(valor: number): void {
        this.saldo += valor;
    }

    public consultarSaldo(): number {
        return this.saldo;
    }
}
```
No exemplo acima, a propriedade `saldo` é privada e só pode ser acessada dentro da classe `ContaBancaria`. Os métodos `depositar` e `consultarSaldo` são públicos e podem ser acessados de fora da classe.
Esses conceitos são fundamentais para criar código modular, reutilizável e seguro em TypeScript. Entender como e quando usar classes, herança, e modificadores de acesso é essencial para qualquer desenvolvedor que queira aproveitar ao máximo a Programação Orientada a Objetos.