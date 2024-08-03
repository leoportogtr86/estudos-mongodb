Claro! Aqui estão 10 exercícios práticos para você praticar a inserção de documentos no MongoDB usando a linha de comando.

### Exercício 1: Inserir um Documento Simples
1. Conecte-se ao MongoDB através do shell `mongo`.
2. Use o banco de dados `empresa`.
3. Insira um documento na coleção `funcionarios` com os seguintes dados: `{ nome: "Alice", idade: 30, cargo: "Desenvolvedora" }`.

### Exercício 2: Inserir Múltiplos Documentos
1. No banco de dados `empresa`, insira vários documentos na coleção `funcionarios` com os seguintes dados:
   - `{ nome: "Bob", idade: 25, cargo: "Designer" }`
   - `{ nome: "Charlie", idade: 35, cargo: "Gerente" }`
   - `{ nome: "Diana", idade: 28, cargo: "Analista de Dados" }`

### Exercício 3: Inserir Documento com Data e Tipo Binário
1. Insira um documento na coleção `projetos` com os seguintes dados:
   - `{ nome: "Projeto Alpha", data_inicio: new Date("2023-01-15"), arquivo: new BinData(0, "base64encodedstring") }`

### Exercício 4: Inserir Documento com Campo Aninhado
1. Insira um documento na coleção `departamentos` com os seguintes dados:
   - `{ nome: "TI", gerente: { nome: "Eve", idade: 40 } }`

### Exercício 5: Inserir Documento com Array
1. Insira um documento na coleção `projetos` com os seguintes dados:
   - `{ nome: "Projeto Beta", equipe: ["Alice", "Bob", "Diana"] }`

### Exercício 6: Inserir Documento em Coleção Capped
1. Crie uma coleção chamada `logs` com as opções `capped: true`, `size: 5242880` (5 MB) e `max: 1000` documentos.
2. Insira um documento na coleção `logs` com os seguintes dados: `{ mensagem: "Erro no sistema", nivel: "critico" }`.

### Exercício 7: Inserir Documento com Validação de Esquema
1. Crie uma coleção chamada `clientes` com validação de esquema para garantir que os documentos tenham os campos `nome` (string) e `idade` (inteiro).
2. Insira um documento na coleção `clientes` com os seguintes dados: `{ nome: "Frank", idade: 33 }`.

### Exercício 8: Inserir Documento com `insertOne` e Opções
1. Insira um documento na coleção `funcionarios` com as opções `writeConcern: { w: "majority", j: true }` e os seguintes dados: `{ nome: "Grace", idade: 27, cargo: "Arquiteta de Software" }`.

### Exercício 9: Inserir Documento com Campos Faltando (e verificar validação)
1. Tente inserir um documento na coleção `clientes` sem o campo `idade` e observe o erro: `{ nome: "Henry" }`.
2. Corrija o documento e insira com os campos completos: `{ nome: "Henry", idade: 45 }`.

### Exercício 10: Inserir Documento em Coleção com Índice Único
1. Crie um índice único no campo `email` da coleção `usuarios`.
2. Insira dois documentos na coleção `usuarios` com os seguintes dados:
   - `{ nome: "Isabel", email: "isabel@example.com" }`
   - `{ nome: "Jack", email: "isabel@example.com" }` (este deve falhar devido à restrição de unicidade).

### Resoluções Detalhadas

#### Exercício 1: Inserir um Documento Simples
```javascript
mongo
use empresa
db.funcionarios.insertOne({ nome: "Alice", idade: 30, cargo: "Desenvolvedora" })
```

#### Exercício 2: Inserir Múltiplos Documentos
```javascript
db.funcionarios.insertMany([
  { nome: "Bob", idade: 25, cargo: "Designer" },
  { nome: "Charlie", idade: 35, cargo: "Gerente" },
  { nome: "Diana", idade: 28, cargo: "Analista de Dados" }
])
```

#### Exercício 3: Inserir Documento com Data e Tipo Binário
```javascript
db.projetos.insertOne({
  nome: "Projeto Alpha",
  data_inicio: new Date("2023-01-15"),
  arquivo: new BinData(0, "base64encodedstring")
})
```

#### Exercício 4: Inserir Documento com Campo Aninhado
```javascript
db.departamentos.insertOne({
  nome: "TI",
  gerente: { nome: "Eve", idade: 40 }
})
```

#### Exercício 5: Inserir Documento com Array
```javascript
db.projetos.insertOne({
  nome: "Projeto Beta",
  equipe: ["Alice", "Bob", "Diana"]
})
```

#### Exercício 6: Inserir Documento em Coleção Capped
```javascript
db.createCollection("logs", { capped: true, size: 5242880, max: 1000 })
db.logs.insertOne({ mensagem: "Erro no sistema", nivel: "critico" })
```

#### Exercício 7: Inserir Documento com Validação de Esquema
```javascript
db.createCollection("clientes", {
  validator: {
    $jsonSchema: {
      bsonType: "object",
      required: ["nome", "idade"],
      properties: {
        nome: {
          bsonType: "string",
          description: "deve ser uma string e é obrigatório"
        },
        idade: {
          bsonType: "int",
          minimum: 0,
          description: "deve ser um inteiro não negativo e é obrigatório"
        }
      }
    }
  }
})
db.clientes.insertOne({ nome: "Frank", idade: 33 })
```

#### Exercício 8: Inserir Documento com `insertOne` e Opções
```javascript
db.funcionarios.insertOne(
  { nome: "Grace", idade: 27, cargo: "Arquiteta de Software" },
  { writeConcern: { w: "majority", j: true } }
)
```

#### Exercício 9: Inserir Documento com Campos Faltando (e verificar validação)
```javascript
// Este comando deve falhar
db.clientes.insertOne({ nome: "Henry" })

// Comando correto
db.clientes.insertOne({ nome: "Henry", idade: 45 })
```

#### Exercício 10: Inserir Documento em Coleção com Índice Único
```javascript
db.usuarios.createIndex({ email: 1 }, { unique: true })
db.usuarios.insertOne({ nome: "Isabel", email: "isabel@example.com" })
// Este comando deve falhar devido à restrição de unicidade
db.usuarios.insertOne({ nome: "Jack", email: "isabel@example.com" })
```

Esses exercícios cobrem uma variedade de cenários para inserir documentos no MongoDB e devem ajudar você a entender melhor as operações básicas de inserção.