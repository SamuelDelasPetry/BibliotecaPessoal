# Interface — Biblioteca de Livros

## 1. Identidade visual

A interface seguirá uma proposta **escura, minimalista e simples**, priorizando a visualização dos livros e das informações de leitura.

O roxo será utilizado como cor de destaque para ações principais, elementos selecionados e informações de progresso.

### Paleta base

* Fundo principal: preto ou cinza muito escuro.
* Superfícies e cards: tons de cinza escuro.
* Texto principal: branco ou cinza claro.
* Texto secundário: cinza.
* Destaques e ações: roxo.

A definição exata dos códigos de cor poderá ser ajustada durante a implementação, mantendo essa identidade visual.

## 2. Tipografia

Será utilizada uma fonte simples e legível, adequada para interfaces mobile.

A hierarquia visual será determinada principalmente por:

* tamanho da fonte;
* peso;
* espaçamento;
* contraste.

## 3. Navegação principal

A aplicação possuirá navegação simples entre as áreas principais:

* **Biblioteca**
* **Wishlist**
* **Perfil**

A biblioteca será a principal tela do aplicativo.

## 4. Biblioteca

A biblioteca exibirá todos os livros cadastrados pelo usuário.

Por padrão, os livros serão organizados priorizando:

1. Lendo
2. Quero ler
3. Lidos

O usuário também poderá filtrar a visualização por estado.

Cada livro poderá ser apresentado em um card contendo:

* capa, quando disponível;
* título;
* autor;
* estado atual;
* informações de progresso quando estiver sendo lido.

Para livros em leitura, será apresentado:

* página atual;
* total de páginas;
* percentual de progresso;
* representação visual do progresso.

## 5. Wishlist

A wishlist apresentará livros que o usuário deseja adicionar futuramente à sua biblioteca.

Ao selecionar um livro, o usuário poderá utilizar a ação **Adicionar à biblioteca**.

Nesse caso, o livro será removido da wishlist e adicionado à biblioteca no estado **Quero ler**.

## 6. Detalhes do livro

Ao selecionar um livro da biblioteca, será exibida sua tela de detalhes.

Ela poderá apresentar:

* capa;
* título;
* autor;
* total de páginas;
* estado;
* progresso atual;
* nota, quando disponível;
* comentário final, quando disponível.

As principais ações serão:

* Registrar leitura;
* Consultar anotações;
* Editar livro;
* Marcar como concluído.

## 7. Registro de leitura

O registro de leitura permitirá informar:

* página inicial;
* página final;
* anotação opcional.

Após o salvamento, o progresso do livro será atualizado.

As anotações poderão posteriormente possuir informações complementares, como:

* página;
* cor;
* tópico ou categoria.

## 8. Anotações

As anotações poderão ser visualizadas em uma área específica do livro, organizadas principalmente pelas páginas às quais estão relacionadas.

Quando disponíveis, filtros poderão permitir a organização por:

* página;
* cor;
* tópico.

## 9. Conclusão da leitura

Ao selecionar **Marcar como concluído**, o usuário poderá realizar uma avaliação final da obra.

A interface solicitará:

* nota de `0` a `10`;
* comentário final sobre o livro.

Após a conclusão, o livro será classificado como **Lido**.

## 10. Diretrizes gerais

A interface deve:

* evitar excesso de informações em uma única tela;
* utilizar componentes e botões consistentes;
* priorizar as ações mais utilizadas;
* apresentar feedback após operações de cadastro ou alteração;
* utilizar estados vazios quando não houver livros ou registros;
* manter o padrão visual entre as diferentes telas.
