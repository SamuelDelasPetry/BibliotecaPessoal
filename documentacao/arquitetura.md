# Arquitetura do Aplicativo

## 1. Visão Geral

O aplicativo será desenvolvido utilizando React Native com TypeScript e utilizará Firebase Firestore para persistência dos dados.

A estrutura do projeto será dividida de acordo com as responsabilidades de cada parte da aplicação, buscando manter separadas a interface, a lógica de acesso aos dados e as definições utilizadas pelo sistema.

## 2. Estrutura

```text
src/
├── components/
├── screens/
├── services/
└── types/
```

### `components/`

Contém componentes visuais reutilizáveis utilizados em diferentes partes da aplicação.

Exemplos:

```text
BookCard.tsx
Rating.tsx
```

### `screens/`

Contém as telas principais da aplicação. Cada tela é responsável pela apresentação das informações e interação com o usuário.

Exemplos:

```text
HomeScreen.tsx
WishlistScreen.tsx
ReadBooksScreen.tsx
BookDetailsScreen.tsx
```

### `services/`

Contém os serviços responsáveis pelo acesso e manipulação dos dados externos da aplicação, principalmente as operações realizadas no Firebase Firestore.

Exemplo:

```text
bookService.ts
```

### `types/`

Contém os tipos e interfaces TypeScript utilizados para representar os dados da aplicação.

Exemplo:

```text
Book.ts
```

## 3. Fluxo de Dados

De forma geral, uma tela ou componente solicita uma operação ao serviço correspondente. O serviço realiza a comunicação com o Firebase Firestore e retorna os dados para a aplicação.

```text
Tela / Componente
       ↓
     Service
       ↓
Firebase Firestore
```

## 4. Padrão de Nomenclatura

Os componentes, telas e tipos utilizarão `PascalCase`.

Exemplos:

```text
BookCard.tsx
HomeScreen.tsx
Book.ts
```

Os arquivos responsáveis por serviços utilizarão `camelCase`.

Exemplo:

```text
bookService.ts
```

As funções e variáveis também utilizarão `camelCase`.
