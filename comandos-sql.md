# Comandos SQL - referencias

## Modelagem de dados com comandos DDL

### Criar banco de dados 

CREATE DATABASE vendas  CHARACTER SET utf8mb4;

### Criar tabela de fabricantes
```sql
CREATE TABLE fabricantes(
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
    preco DECIMAL(6,2) NOT NULL,
    fabricante_id INT NOT NULL 
);
```
### Criação de relacionamnto entre tabelas (chave estrangeira)

```sql
ALTER TABLE produtos
    ADD CONSTRAINT fk_produtos_fabricantes
    FOREIGN KEY (fabricante_id) REFERENCES fabricantes(id);  

```

### Exemplo de alteração na tabela 
```sql
ALTER TABLE fabricantes RENAME TO fornecedores;
```
### Modificar colunas 
```sql
ALTER TABLE produtos 
    MODIFY COLUMN preco DECIMAL(6,2) NOT NULL;

ALTER TABLE fabricantes 
    CHANGE nome nome_do_fabricante VARCHAR(20) NOT NULL;    
```
### adicionar coluna

```sql
ALTER TABLE produtos 
    ADD quantidade INT NULL AFTER preco;    
```