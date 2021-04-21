# Trilha React
- react-dom: integração do react com o dom

## Principais conceitos

### Componente:
- Conceito __muito importante__
- É basicamente uma função que __retorna HTML__
- A ideia de componentização corrobora com o __reúso__
- A ideia de componentização corrobora com a __modularização__
### Propriedade:
- É a __informação(dado)__ que é passada de um componente para o outro
  - **Fragment**:
    - Utilizado para abraçar componentes que estão "no mesmo nível"
- Conceito de JSX: 
  - Código javascript no html
  - Código deve ser "abraçado" por chaves
```javascript
export default function MyComponent(props) {
  return (
    <button>{props.title}</button>
  )
})
```
- Propriedade global __children__:
  - É o conteúdo dentro da tag, não há nome para a propriedade(dado)
  - Informação definida automaticamente pelo __React__

### Conceito de estado:
- Forma de manipular informações de dentro de um componente
- Exemplo:
  > - Ao clicar em um botão, botar a informação dentro dele
  ```javascript
  export default function Button(props) {
    let counter = 1;

    function increment() {
      counter += 1;
    }

    return ( 
      <>
        <span>{counter}</span>
        <button onClick={increment}>{props.children}</button>
        <br />
      </>
    )
  }
  ```
  > Nesse code snippet acima o valor do counter não será alterado, pois o React não fica monitorando o valor das variáveis, ou seja, mesmo que o valor de counter mude, não aparecerá na tela a mudança. Para que isso aconteça, é necessário utilizar o conceito de estado.
  ```javascript
  import { useState } from 'react';

  export default function Button(props) {
    const [counter, setCounter] = useState(1);
    // Na linha de cima, ocorre desestruturação
    // Dado retornado pelo useState: [estado, alterarEstado]

    function increment() {
      setCounter(counter + 1);
    }

    return ( 
      <>
        <span>{counter}</span>
        <button onClick={increment}>{props.children}</button>
        <br />
      </>
    )
  }
  ```
  > Agora sim, o valor exibido é alterado. 

## Problemas enfrentados pelo React
- Quando o Javascript está desabilitado, nada é exibido
- Toda busca de dados da aplicação, na verdade, literalmente tudo acontece através do Javascript, e pelo Javascript que está rodando pelo __browser__, ou seja, __client-side__, o Javascript só é executado quando o cliente executa a nossa página.