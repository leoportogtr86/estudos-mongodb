### Exercício 1: Criar uma Coleção Implicitamente
1. Conecte-se ao MongoDB através do shell `mongo`.
2. Use o banco de dados `exercicios`.
3. Insira um documento na coleção `alunos` com os seguintes dados: `{ nome: "Pedro", idade: 21, curso: "Engenharia" }`.

### Exercício 2: Criar uma Coleção Explicitamente
1. No banco de dados `exercicios`, crie uma coleção chamada `professores`.
2. Verifique a criação da coleção listando todas as coleções no banco de dados.

### Exercício 3: Criar uma Coleção com Opções
1. Crie uma coleção chamada `logs` com as opções `capped: true`, `size: 1048576` (1 MB) e `max: 1000` documentos.
2. Verifique a criação da coleção e suas opções.

### Exercício 4: Inserir Vários Documentos
1. Insira múltiplos documentos na coleção `professores` com os seguintes dados:
   - `{ nome: "Dr. Silva", departamento: "Matemática" }`
   - `{ nome: "Dr. Costa", departamento: "Física" }`
   - `{ nome: "Dr. Souza", departamento: "Química" }`
2. Liste todos os documentos na coleção `professores` para verificar a inserção.

### Exercício 5: Consultar Documentos com Critérios
1. Consulte e exiba todos os documentos na coleção `alunos` onde o curso é "Engenharia".
2. Consulte e exiba todos os documentos na coleção `professores` onde o departamento é "Física".

### Exercício 6: Atualizar Documentos
1. Atualize o documento do professor "Dr. Silva" para que seu departamento seja "Estatística".
2. Verifique a atualização listando todos os documentos na coleção `professores`.

### Exercício 7: Excluir Documentos
1. Exclua o documento do aluno "Pedro".
2. Verifique a exclusão listando todos os documentos na coleção `alunos`.

### Exercício 8: Criar e Gerenciar Índices
1. Crie um índice no campo `nome` da coleção `professores`.
2. Liste todos os índices na coleção `professores` para verificar a criação.

### Exercício 9: Excluir Índices
1. Exclua o índice criado no exercício anterior no campo `nome` da coleção `professores`.
2. Verifique a exclusão listando todos os índices na coleção `professores`.

### Exercício 10: Excluir uma Coleção
1. Exclua a coleção `logs`.
2. Verifique a exclusão listando todas as coleções no banco de dados `exercicios`.

### Resoluções Detalhadas

#### Exercício 1: Criar uma Coleção Implicitamente
```bash
mongo
use exercicios
db.alunos.insertOne({ nome: "Pedro", idade: 21, curso: "Engenharia" })
```

#### Exercício 2: Criar uma Coleção Explicitamente
```javascript
db.createCollection("professores")
show collections
```

#### Exercício 3: Criar uma Coleção com Opções
```javascript
db.createCollection("logs", { capped: true, size: 1048576, max: 1000 })
```

#### Exercício 4: Inserir Vários Documentos
```javascript
db.professores.insertMany([
  { nome: "Dr. Silva", departamento: "Matemática" },
  { nome: "Dr. Costa", departamento: "Física" },
  { nome: "Dr. Souza", departamento: "Química" }
])
db.professores.find().pretty()
```

#### Exercício 5: Consultar Documentos com Critérios
```javascript
db.alunos.find({ curso: "Engenharia" }).pretty()
db.professores.find({ departamento: "Física" }).pretty()
```

#### Exercício 6: Atualizar Documentos
```javascript
db.professores.updateOne(
  { nome: "Dr. Silva" },
  { $set: { departamento: "Estatística" } }
)
db.professores.find().pretty()
```

#### Exercício 7: Excluir Documentos
```javascript
db.alunos.deleteOne({ nome: "Pedro" })
db.alunos.find().pretty()
```

#### Exercício 8: Criar e Gerenciar Índices
```javascript
db.professores.createIndex({ nome: 1 })
db.professores.getIndexes()
```

#### Exercício 9: Excluir Índices
```javascript
db.professores.dropIndex("nome_1")
db.professores.getIndexes()
```

#### Exercício 10: Excluir uma Coleção
```javascript
db.logs.drop()
show collections
```

Esses exercícios ajudarão você a praticar a criação e gerenciamento de coleções no MongoDB, cobrindo inserções, consultas, atualizações, exclusões e gerenciamento de índices.