# Sistema Customizado: Casos de Uso

---

## 1. Descrição do Sistema

O sistema customizado da **NATALAB** é projetado para facilitar o gerenciamento de clientes e instrumentos, além de garantir a entrada e visualização dos dados de calibração de maneira eficiente e segura. O sistema oferece uma interface amigável para a equipe da NATALAB e seus clientes, permitindo o acesso a relatórios, a visualização de dados e a emissão de documentos em formato PDF.

---

## 2. Casos de Uso

### Caso de Uso: **Cadastro de Clientes**

- **Ator Principal**: Administrador
- **Descrição**: O administrador pode cadastrar novos clientes com informações como nome, CNPJ, endereço e contato. Os clientes podem posteriormente visualizar seus instrumentos e relatórios.
- **Ação Principal**: O administrador insere os dados no formulário e os salva no sistema, associando-os a um cliente.

### Caso de Uso: **Cadastro de Instrumentos**

- **Ator Principal**: Administrador
- **Descrição**: O administrador cadastra instrumentos pertencentes a cada cliente. Os instrumentos são identificados por número de série, marca, modelo e outras características.
- **Ação Principal**: O administrador associa um instrumento a um cliente e insere seus dados.

### Caso de Uso: **Entrada de Dados de Calibração**

- **Ator Principal**: Técnico de Calibração
- **Descrição**: O técnico insere os resultados de calibrações, datas e observações relevantes, diretamente no sistema para cada instrumento.
- **Ação Principal**: O técnico seleciona o cliente e o instrumento, insere os dados de calibração e os salva.

### Caso de Uso: **Visualização de Dados**

- **Ator Principal**: Cliente
- **Descrição**: O cliente, após login, pode visualizar os dados dos instrumentos e os resultados das calibrações realizadas.
- **Ação Principal**: O cliente acessa seu painel de controle e visualiza a lista de instrumentos, podendo clicar em cada um para ver os detalhes.

### Caso de Uso: **Filtro por Características de Equipamento**

- **Ator Principal**: Cliente
- **Descrição**: O cliente pode filtrar seus instrumentos por características como marca, modelo e status de calibração.
- **Ação Principal**: O cliente aplica os filtros e visualiza os resultados.

### Caso de Uso: **Impressão de PDF**

- **Ator Principal**: Cliente
- **Descrição**: O cliente pode gerar relatórios em PDF com os dados de calibração de seus instrumentos.
- **Ação Principal**: O cliente clica no botão de geração de PDF e o sistema prepara o arquivo com as informações do instrumento selecionado.

---

## 3. Diagrama UML de Casos de Uso

```mermaid
flowchart LR
    A[Administrador] --> B[Cadastro de Clientes]
    A --> C[Cadastro de Instrumentos]
    
    B --> D[Gerenciamento de Clientes]
    C --> E[Gerenciamento de Instrumentos]
    
    F[Técnico de Calibração] --> G[Entrada de Dados de Calibração]
    G --> E
    
    H[Cliente] --> I[Visualização de Instrumentos]
    H --> J[Filtro por Características de Equipamento]
    H --> K[Impressão de Relatórios PDF]
    
    I --> E
    J --> E
    K --> E
```

---

## 4. Diagramas de Sequência

### Diagrama de Sequência: Cadastro de Clientes

```mermaid
sequenceDiagram
    participant Admin as Administrador
    participant Sistema
    participant DB as Banco de Dados
    
    Admin->>Sistema: Preenche dados do cliente
    Sistema->>DB: Salva dados do cliente
    DB-->>Sistema: Confirmação de salvamento
    Sistema-->>Admin: Exibe mensagem de sucesso
```

### Diagrama de Sequência: Cadastro de Instrumentos

```mermaid
sequenceDiagram
    participant Admin as Administrador
    participant Sistema
    participant DB as Banco de Dados
    
    Admin->>Sistema: Preenche dados do instrumento
    Sistema->>DB: Salva dados do instrumento
    DB-->>Sistema: Confirmação de salvamento
    Sistema-->>Admin: Exibe mensagem de sucesso
```

### Diagrama de Sequência: Entrada de Dados de Calibração

```mermaid
sequenceDiagram
    participant Tecnico as Técnico de Calibração
    participant Sistema
    participant DB as Banco de Dados
    
    Tecnico->>Sistema: Insere dados de calibração
    Sistema->>DB: Salva dados de calibração
    DB-->>Sistema: Confirmação de salvamento
    Sistema-->>Tecnico: Exibe mensagem de sucesso
```

### Diagrama de Sequência: Visualização de Dados

```mermaid
sequenceDiagram
    participant Cliente
    participant Sistema
    participant DB as Banco de Dados
    
    Cliente->>Sistema: Solicita visualização de dados dos instrumentos
    Sistema->>DB: Consulta dados dos instrumentos
    DB-->>Sistema: Retorna dados dos instrumentos
    Sistema-->>Cliente: Exibe dados na interface
```

### Diagrama de Sequência: Filtro por Características de Equipamento

```mermaid
sequenceDiagram
    participant Cliente
    participant Sistema
    participant DB as Banco de Dados
    
    Cliente->>Sistema: Aplica filtro (marca, modelo, etc.)
    Sistema->>DB: Consulta dados filtrados
    DB-->>Sistema: Retorna dados filtrados
    Sistema-->>Cliente: Exibe dados filtrados
```

### Diagrama de Sequência: Impressão de Relatório PDF

```mermaid
sequenceDiagram
    participant Cliente
    participant Sistema
    participant PDFGen as Gerador de PDF
    
    Cliente->>Sistema: Solicita relatório em PDF
    Sistema->>PDFGen: Gera PDF com dados do instrumento
    PDFGen-->>Sistema: Retorna arquivo PDF
    Sistema-->>Cliente: Disponibiliza PDF para download
```

---

### Explicação dos Diagramas

- **Cadastro de Clientes/Instrumentos**: O administrador insere os dados, que são salvos no banco de dados, e uma confirmação é exibida.
- **Entrada de Dados de Calibração**: O técnico insere os dados de calibração que são salvos no banco.
- **Visualização e Filtro de Dados**: O cliente solicita dados dos instrumentos e o sistema retorna as informações filtradas ou não, dependendo da interação.
- **Impressão de Relatório**: O cliente solicita a geração de um relatório em PDF, que é gerado e disponibilizado para download.

Esses diagramas mostram o fluxo de comunicação entre os diferentes atores e o sistema, com as interações com o banco de dados e outras funcionalidades.