# Azure Storage SFTP – Multi-User Folder Isolation

Implementação de um **servidor SFTP baseado em Azure Storage Account**, permitindo que múltiplos usuários acessem **somente suas próprias pastas** dentro de um container.

Esta solução utiliza:

- Azure Storage Account com **SFTP habilitado**
- **Local Users**
- **Hierarchical Namespace (Data Lake Gen2)**
- **ACL POSIX**

## Objetivo

- Automatizar criação de usuários
- Criar estrutura de diretórios
- Isolar acesso por pasta
- Gerar credenciais automaticamente

---

# Arquitetura

Estrutura utilizada no container:

```
data-container
│
├── config
│
├── inbound
│   ├── user1
│   ├── user2
│   └── user3
│
└── outbound
    ├── user1
    ├── user2
    └── user3
```

Cada usuário:

- possui **home directory em `inbound/{usuario}`**
- possui **acesso RW somente à sua pasta**

---

# Pré-requisitos

### 1️⃣ Azure CLI instalada

```bash
az version
```

### 2️⃣ Login na subscription

```bash
az login
```

### 3️⃣ Storage Account com:

- **SFTP habilitado**
- **Hierarchical Namespace habilitado**

### 4️⃣ Permissões necessárias

- `Storage Blob Data Owner`

ou

- `Storage Blob Data Contributor`

---

# Variáveis utilizadas

```bash
STORAGE_ACCOUNT=storageaccountname
RESOURCE_GROUP=resource-group-name
CONTAINER=data-container
```

---

# Arquivo de usuários

Criar um arquivo chamado **`users.txt`**

```
user1
user2
user3
```

Cada linha representa um **usuário SFTP**.
