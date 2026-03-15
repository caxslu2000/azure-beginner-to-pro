# Azure Storage SFTP – Multi-User Folder Isolation

Implementation of an **SFTP server based on an Azure Storage Account**, allowing multiple users to access **only their own folders** within a container.

This solution uses:

- Azure Storage Account with **SFTP enabled**
- **Local Users**
- **Hierarchical Namespace (Data Lake Gen2)**
- **POSIX ACL**

## Objective

- Automate user creation
- Create directory structures
- Isolate folder access per user
- Automatically generate credentials

---

# Architecture

Container structure used in this implementation:

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

Each user:

- has their **home directory set to `inbound/{username}`**
- has **read/write (RW) access only to their own folder**

---

# Prerequisites

### 1️⃣ Azure CLI installed

```bash
az version
```

### 2️⃣ Login to the subscription

```bash
az login
```

### 3️⃣ Storage Account configured with:

- **SFTP enabled**
- **Hierarchical Namespace enabled**

### 4️⃣ Required permissions

- `Storage Blob Data Owner`

or

- `Storage Blob Data Contributor`

---

# Variables Used

```bash
STORAGE_ACCOUNT=storageaccountname
RESOURCE_GROUP=resource-group-name
CONTAINER=data-container
```

---

# Users File

Create a file called **`users.txt`**

```
user1
user2
user3
```

Each line represents an **SFTP user**.
