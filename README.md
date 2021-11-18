# CheckList-Redux
Check-List
*Antes de começar*
- [ ] pensar como será o *formato* do seu estado global
- [ ] pensar quais actions serão necessárias na sua aplicação
​
*Instalação*
- [ ] npx create-react-app my-app-redux;
- [ ] npm i react-redux;
- [ ] npm i redux-devtools-extension; 
- [ ] npm install.
- [ ] ou npm install prop-types react-redux redux redux-logger redux-thunk.
​
*Criar dentro do diretório src:*
- [ ] diretório actions;
- [ ] diretório reducers;
- [ ] diretório store.
​
*Criar dentro do diretório actions:*
- [ ] arquivo index.js.
​
``` modelo de código
// ===== ACTION TYPES =====
    export const EXEMPLO = 'EXEMPLO'
    export const EXEMPLO2 = 'EXEMPLO2'
​
// ===== ACTIONS ===== PODE SER MAIS DE UMA.
​
    export const <nomedaAction> = (payload 'carga de informações') => (
      {
        type: EXEMPLO,
        payload,
      }
    )
 ``` 
​
*Criar dentro do diretório reducers:*
- [ ] arquivo index.js. para o rootReducer
- [ ] os seus reducers.
​
``` REDUCES 
## O arquivo do combine reducers ##
​
import { combineReducers } from 'redux';
import myReducer from 'caminho do arquivo';
​
const rootReducer = combineReducers({ myReducer });
​
export default rootReducer;
​
## O REDUCER ##
​
// PRECISO IMPORTAR A ACTION PRA CA.
import { <NOME DAS ACTIONS> } from '<CAMINHO DA ACTION>'
​
const INITIAL_STATE = {
  state: '',
};
​
function <NOME DO REDUCER>(state = INITIAL_STATE, action) {
  switch (action.type) {
    case <ACTION TYPE>:
      return { 
// para conservar o estado anterior uso um spread, para garantir que será criado um novo local na memória.
        ...state,
        keyState: action.state };
    default:
      return state;
  }
}
​
export default <NOME DO REDUCER>;
​
```
​
*Criar dentro do diretório store:*
- [ ] arquivo index.js.
​
``` STORE
import { createStore, applyMiddleware } from 'redux';
import { composeWithDevTools } from 'redux-devtolls-extension';
import thunk from 'redux-thunk';
import rootReducer from '../caminho do arquivo';
​
const store = createStore(rootReducer, composeWithDevTolls(
  applyMidlleware(thunk)
));
​
export default store;
​
```
​
*No arquivo App.js, ou no index.js*
- [ ] definir o Provider, `<Provider store={ store }>`, para fornecer os estados à todos os componentes encapsulados em `<App />`.
​
*No arquivo store/index.js:*
- [ ] importar o rootReducer e criar a store
- [ ] configurar o [Redux DevTools](https://github.com/reduxjs/redux-devtools)
​
*Na pasta reducers:*
- [ ] criar os reducers necessários
- [ ] configurar os exports do arquivo index.js
​
*Na pasta actions:*
- [ ] criar os actionTypes, por exemplo: `const ADD_TO_CART = 'ADD_TO_CART';`
- [ ] criar os actions creators necessários
​
*Nos componentes:*
- [ ] criar a função mapStateToProps
``` STATE - PROPS
const mapStateToProps = (state) => ({
  chaveExemplo: state.reducer.<nome da chave dentro do reducer>
// se você não estiver usando combine reducer, não é necessário utilizar o nome do reducer, faça apenas:
  chaveExemplo: state.<nome da chave>
});
​
 ```
​
- [ ] criar a função mapDispatchToProps
​
``` DISPATCHPROPS
const mapDispatchToProps = (dispatch) => {
  return ({
    exemploChave: (<valor da sua action>) => dispatch(<nome da acton>(<valor da action>)),
  })
};
 ```
​
- [ ] fazer o connect
​
``` CONNECT
** IMPORTE O CONNECT **
​
export default connect(mapStateToprops, mapDispatchToProps) (<Nome do Arquivo>)
 ```
