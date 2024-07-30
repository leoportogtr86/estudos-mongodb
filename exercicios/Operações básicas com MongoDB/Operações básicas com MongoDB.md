### Exercício 1: Criar um Banco de Dados
1. Conecte-se ao MongoDB através do shell `mongo`.
2. Crie um banco de dados chamado `escola`.
3. Verifique a criação do banco de dados listando todos os bancos de dados disponíveis.

### Exercício 2: Criar e Inserir Dados em uma Coleção
1. No banco de dados `escola`, crie uma coleção chamada `alunos`.
2. Insira um documento com as seguintes informações: `{ nome: "João", idade: 18, curso: "Matemática" }`.
3. Verifique a inserção listando todos os documentos na coleção `alunos`.

### Exercício 3: Inserir Múltiplos Documentos
1. Insira vários documentos na coleção `alunos` com os seguintes dados:
   - `{ nome: "Maria", idade: 20, curso: "Física" }`
   - `{ nome: "Carlos", idade: 22, curso: "Química" }`
   - `{ nome: "Ana", idade: 19, curso: "Biologia" }`
2. Verifique a inserção listando todos os documentos na coleção `alunos`.

### Exercício 4: Consultar Documentos
1. Consulte e exiba todos os documentos na coleção `alunos`.
2. Consulte e exiba apenas os documentos onde o curso é "Matemática".

### Exercício 5: Atualizar Documentos
1. Atualize o documento do aluno "João" para que sua idade seja 19.
2. Verifique a atualização listando todos os documentos na coleção `alunos`.

### Exercício 6: Atualizar Múltiplos Documentos
1. Atualize todos os documentos na coleção `alunos` onde a idade é maior que 20, mudando o campo `curso` para "Engenharia".
2. Verifique a atualização listando todos os documentos na coleção `alunos`.

### Exercício 7: Excluir Documentos
1. Exclua o documento do aluno "Ana".
2. Verifique a exclusão listando todos os documentos na coleção `alunos`.

### Exercício 8: Excluir Múltiplos Documentos
1. Exclua todos os documentos na coleção `alunos` onde o curso é "Engenharia".
2. Verifique a exclusão listando todos os documentos na coleção `alunos`.

### Exercício 9: Criar Índices
1. Crie um índice no campo `nome` da coleção `alunos`.
2. Verifique a criação do índice listando todos os índices na coleção `alunos`.

### Exercício 10: Excluir um Banco de Dados
1. Exclua o banco de dados `escola`.
2. Verifique a exclusão listando todos os bancos de dados disponíveis.

Esses exercícios cobrem as operações básicas de criação, consulta, atualização, exclusão e gerenciamento de índices em MongoDB puro usando o shell do MongoDB.