Tabela com os principais parâmetros que podem ser passados ao criar uma coleção no MongoDB, juntamente com uma breve descrição de cada um.

| **Parâmetro**           | **Tipo**  | **Descrição**                                                                                  |
|-------------------------|-----------|-----------------------------------------------------------------------------------------------|
| `capped`                | Boolean   | Define se a coleção é limitada. Coleções limitadas têm um tamanho fixo e atuam como um buffer circular. |
| `size`                  | Integer   | Especifica o tamanho máximo em bytes para uma coleção limitada. Necessário se `capped` for true.          |
| `max`                   | Integer   | Define o número máximo de documentos para uma coleção limitada.                                             |
| `validator`             | Document  | Define as regras de validação de esquema para os documentos inseridos na coleção.                             |
| `validationLevel`       | String    | Determina o nível de validação dos documentos. Pode ser "off", "strict" ou "moderate".                    |
| `validationAction`      | String    | Determina a ação a ser tomada quando a validação falha. Pode ser "error" ou "warn".                       |
| `storageEngine`         | Document  | Especifica as configurações específicas do mecanismo de armazenamento.                                      |
| `indexOptionDefaults`   | Document  | Define as configurações padrão de opções de índice para a coleção.                                          |
| `viewOn`                | String    | Especifica a coleção ou visualização subjacente a partir da qual a visualização será criada.               |
| `pipeline`              | Array     | Especifica o pipeline de agregação que define a visualização.                                              |
| `collation`             | Document  | Especifica as regras de collation (ordenação e comparação) para a coleção.                                  |
| `writeConcern`          | Document  | Define o nível de confirmação da escrita.                                                                  |
| `timeseries`            | Document  | Define a coleção como uma coleção de séries temporais e especifica as opções de séries temporais.           |
| `expireAfterSeconds`    | Integer   | Define o tempo de vida (TTL) dos documentos na coleção.                                                    |
| `clusteredIndex`        | Document  | Especifica a configuração do índice clusterizado para a coleção.                                            |
| `changeStreamPreAndPostImages` | Document  | Configura a coleção para armazenar imagens pré e pós mudança dos documentos para streams de mudanças.       |

### Exemplos de Uso

#### Criando uma Coleção Limitada (Capped Collection)
```javascript
db.createCollection("logs", { capped: true, size: 5242880, max: 5000 })
```

#### Criando uma Coleção com Validação de Esquema
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
  },
  validationLevel: "strict",
  validationAction: "error"
})
```

#### Criando uma Visualização (View)
```javascript
db.createCollection("resumoDeVendas", {
  viewOn: "vendas",
  pipeline: [
    { $match: { status: "Aprovado" } },
    { $group: { _id: "$produtoId", totalVendas: { $sum: "$quantidade" } } }
  ]
})
```

#### Criando uma Coleção com Configurações de Collation
```javascript
db.createCollection("usuarios", {
  collation: { locale: "pt", strength: 2 }
})
```

#### Criando uma Coleção de Séries Temporais
```javascript
db.createCollection("medicoes", {
  timeseries: {
    timeField: "timestamp",
    metaField: "sensorId",
    granularity: "minutes"
  },
  expireAfterSeconds: 31536000 // 1 ano
})
```

Essa tabela e os exemplos devem ajudar você a entender e usar os principais parâmetros ao criar coleções no MongoDB.