# Requisitos — Biblioteca de Livros

**Origem:** `documentacao/visao.md`

## Lista de requisitos

> Convenções:
>
> * **Tipo:** RF (Funcional)
> * **Prioridade:** Must (MVP) / Should (importante) / Could (desejável)

| ID    | Tipo | Nome                              | Descrição                                                                                     | Prioridade | Critério de aceite                                              |
| ----- | ---- | --------------------------------- | --------------------------------------------------------------------------------------------- | ---------- | --------------------------------------------------------------- |
| RF-01 | RF   | Cadastrar usuário                 | Permitir que o usuário crie uma conta no aplicativo.                                          | Must       | Usuário consegue realizar cadastro com dados válidos.           |
| RF-02 | RF   | Autenticar usuário                | Permitir login e logout no aplicativo.                                                        | Must       | Usuário autenticado consegue acessar seus próprios dados.       |
| RF-03 | RF   | Cadastrar livro                   | Permitir cadastrar manualmente um livro com título, autor, total de páginas e capa opcional.  | Must       | Livro válido é persistido e exibido na biblioteca.              |
| RF-04 | RF   | Gerenciar livro                   | Permitir visualizar, editar e remover livros cadastrados.                                     | Must       | Alterações são persistidas e refletidas na biblioteca.          |
| RF-05 | RF   | Organizar biblioteca              | Classificar livros da biblioteca como **Quero ler**, **Lendo** ou **Lido**.                   | Must       | Cada livro da biblioteca possui um único estado.                |
| RF-06 | RF   | Listar biblioteca                 | Exibir os livros do usuário, priorizando livros em leitura e permitindo filtragem por estado. | Must       | Biblioteca apresenta livros do usuário na organização definida. |
| RF-07 | RF   | Adicionar à wishlist              | Permitir cadastrar um livro na lista de desejos.                                              | Must       | Livro passa a ser exibido na wishlist.                          |
| RF-08 | RF   | Mover da wishlist para biblioteca | Permitir adicionar um livro da wishlist à biblioteca no estado **Quero ler**.                 | Must       | Livro deixa a wishlist e passa para a biblioteca.               |
| RF-09 | RF   | Remover da wishlist               | Permitir remover um livro da lista de desejos.                                                | Must       | Livro deixa de aparecer na wishlist.                            |
| RF-10 | RF   | Registrar leitura                 | Permitir registrar uma sessão de leitura informando página inicial e página final.            | Must       | Registro válido é salvo e associado ao livro.                   |
| RF-11 | RF   | Acompanhar progresso              | Exibir página atual, total de páginas e percentual de progresso de livros em leitura.         | Must       | Progresso é atualizado a partir dos registros de leitura.       |
| RF-12 | RF   | Registrar anotação                | Permitir adicionar uma anotação opcional a um registro de leitura.                            | Should     | Registro pode ser salvo com ou sem anotação.                    |
| RF-13 | RF   | Classificar anotação              | Permitir informar página, cor e tópico/categoria para uma anotação.                           | Could      | Informações opcionais podem ser associadas à anotação.          |
| RF-14 | RF   | Consultar anotações               | Permitir visualizar as anotações de um livro e filtrá-las por informações disponíveis.        | Should     | Usuário consegue consultar as anotações vinculadas ao livro.    |
| RF-15 | RF   | Concluir leitura                  | Permitir marcar um livro como concluído.                                                      | Must       | Livro passa para o estado **Lido**.                             |
| RF-16 | RF   | Avaliar livro                     | Permitir atribuir ao livro concluído uma nota numérica de `0` a `10`.                         | Must       | Nota válida é salva e exibida no livro.                         |
| RF-17 | RF   | Registrar comentário final        | Permitir registrar um comentário geral sobre a obra ao concluir a leitura.                    | Must       | Comentário final é associado à leitura concluída.               |
| RF-18 | RF   | Consultar livros lidos            | Permitir consultar livros concluídos com suas notas e comentários finais.                     | Must       | Livros lidos são exibidos com suas avaliações.                  |

## Regras de negócio

### RN-01 — Dados mínimos do livro

* O título é obrigatório.
* O total de páginas deve ser um número inteiro positivo quando informado.
* A capa do livro é opcional.

### RN-02 — Estado do livro

Um livro da biblioteca deve possuir exatamente um dos estados:

* `QUERO_LER`;
* `LENDO`;
* `LIDO`.

### RN-03 — Wishlist e biblioteca

* Um livro da wishlist ainda não pertence à biblioteca.
* Ao utilizar **Adicionar à biblioteca**, o livro:

  * é removido da wishlist;
  * é adicionado à biblioteca como `QUERO_LER`.

### RN-04 — Início da leitura

* Ao registrar uma leitura de um livro que está como `QUERO_LER`, seu estado passa para `LENDO`.

### RN-05 — Registro de páginas

* `pagina_inicial >= 1`.
* `pagina_final >= pagina_inicial`.
* Se o total de páginas do livro estiver definido, `pagina_final <= total_paginas`.

### RN-06 — Progresso da leitura

Quando houver total de páginas:

* a página atual é baseada no progresso registrado;
* `percentual = pagina_atual / total_paginas * 100`;
* o percentual não deve ultrapassar `100%`.

### RN-07 — Conclusão

Ao concluir uma leitura:

* o livro passa para `LIDO`;
* o usuário pode registrar sua avaliação final;
* o progresso é considerado concluído.

### RN-08 — Nota

* A nota deve ser numérica.
* `nota >= 0`.
* `nota <= 10`.

### RN-09 — Anotações

* Uma anotação pertence a um registro de leitura.
* Texto, página, cor e tópico podem ser utilizados para complementar a anotação conforme a funcionalidade disponível.

### RN-10 — Dados por usuário

* Cada usuário deve visualizar e manipular apenas sua própria biblioteca, wishlist, registros e anotações.

## Evoluções possíveis

Não fazem parte obrigatória do MVP:

* múltiplas releituras independentes do mesmo livro;
* categorias personalizadas avançadas;
* pesquisa automática de livros por APIs externas;
* compartilhamento de avaliações;
* estatísticas avançadas de leitura.
