# Comandos SQL - referencias

## Modelagem de dados com comandos DDL

### Criar banco de dados 

CREATE DATABASE vendas  CHARACTER SET utf8mb4;

### Criar tabela de fabricantes
```sql
CRTEATE TABLE fabricantes(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL
);
```

### Vizuaizar detalhes estruturais da tabela    

```sql
DESC fabricantes;

```

```sql
CREATE TABLE produtos(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL,  
    descricao TEXT(500) NULL,
    preco DECIMAL(6,2),
    fabricante_id INT NOT NULL 
);


```
