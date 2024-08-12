# TypeScript com React

TypeScript melhora significativamente a experiência de desenvolvimento em projetos React, fornecendo tipagem estática, melhor autocompletar e detecção precoce de erros. Nesta seção, veremos como configurar e utilizar TypeScript em um projeto React.

## Configurando um Projeto React com TypeScript

Para criar um novo projeto React com suporte a TypeScript, você pode usar o `create-react-app` com o template TypeScript:

```bash
npx create-react-app my-app --template typescript
```

Esse comando cria um novo projeto React com todos os arquivos necessários já configurados para usar TypeScript.

## Componentes com Tipagem 

Vamos ver como podemos tipar componentes funcionais e de classe em React usando TypeScript.

### Componentes Funcionais 
Componentes funcionais em TypeScript são simples de tipar usando a interface `React.FC` (Function Component) ou explicitamente definindo os tipos de `props`.**Exemplo:** 

```typescript
import React from 'react';

interface SaudacaoProps {
    nome: string;
}

const Saudacao: React.FC<SaudacaoProps> = ({ nome }) => {
    return <h1>Olá, {nome}!</h1>;
};

export default Saudacao;
```
Nesse exemplo, a interface `SaudacaoProps` define que o componente `Saudacao` espera uma prop `nome` do tipo `string`.
### Componentes de Classe 

Componentes de classe também podem ser tipados, especialmente em projetos mais antigos ou onde você prefere usar a abordagem de classes.
**Exemplo:** 

```typescript
import React, { Component } from 'react';

interface ContadorProps {
    valorInicial?: number;
}

interface ContadorState {
    valor: number;
}

class Contador extends Component<ContadorProps, ContadorState> {
    static defaultProps = {
        valorInicial: 0,
    };

    state: ContadorState = {
        valor: this.props.valorInicial!,
    };

    incrementar = () => {
        this.setState({ valor: this.state.valor + 1 });
    };

    render() {
        return (
            <div>
                <p>Valor: {this.state.valor}</p>
                <button onClick={this.incrementar}>Incrementar</button>
            </div>
        );
    }
}

export default Contador;
```
Aqui, `ContadorProps` define as props e `ContadorState` define o estado do componente. A tipagem garante que você manipule `props` e `state` de forma segura.
## Tipagem de Eventos 

Em React, você frequentemente lidará com eventos, e TypeScript pode tipá-los para garantir que você manipule os eventos corretamente.
**Exemplo:** 

```typescript
const Botao: React.FC = () => {
    const handleClick = (event: React.MouseEvent<HTMLButtonElement>) => {
        console.log('Botão clicado!', event.currentTarget);
    };

    return <button onClick={handleClick}>Clique-me!</button>;
};
```
Aqui, `React.MouseEvent<HTMLButtonElement>` define que o evento é um evento de mouse disparado por um botão HTML.
## Uso de Context API com TypeScript 

O React Context API também pode ser usado com TypeScript para garantir a tipagem correta dos valores compartilhados.
**Exemplo:** 

```typescript
interface Tema {
    background: string;
    color: string;
}

const TemaContext = React.createContext<Tema | undefined>(undefined);

const App: React.FC = () => {
    const tema: Tema = {
        background: 'lightblue',
        color: 'darkblue',
    };

    return (
        <TemaContext.Provider value={tema}>
            <ComponenteFilho />
        </TemaContext.Provider>
    );
};

const ComponenteFilho: React.FC = () => {
    const tema = React.useContext(TemaContext);

    if (!tema) {
        return <div>Erro: Tema não encontrado!</div>;
    }

    return (
        <div style={{ background: tema.background, color: tema.color }}>
            Este é um componente com tema!
        </div>
    );
};
```
Neste exemplo, `TemaContext` é criado com uma interface `Tema` que define as propriedades esperadas no contexto.
## Conclusão 

Integrar TypeScript em um projeto React oferece muitas vantagens, como tipagem estática, melhor suporte a ferramentas e maior segurança em projetos de longo prazo. Com TypeScript, você pode evitar muitos erros comuns e melhorar a manutenção do seu código React.