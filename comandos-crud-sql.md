# Comandos para operações CRUD no banco de dados    

## Resumo 

C -> CREATE (inserir dados usando comandos `insert`)
R -> READ (ler dados usando comandos`select`)
U -> UPDATE (atualizar dados usando comandos `ùpdate`)
D -> DELETE (excluir dados usando comando `delete`)

## Insert

```sql
insert into fabricantes (nome) values('Asus');

insert into fabricantes (nome) values('Dell');
insert into fabricantes (nome) values('Apple');

insert into fabricantes (nome) values('LG'),('Samsung'),('Brastemp');
insert into fabricantes (nome) values('Positivo'),('Microsoft');
```
## produtos

```sql
insert into produtos(nome,preco,descricao,quantidade,fabricantes_id) values("ultrabook", 3.500, "Equipamento de ultima geração", 7 , 2 );

insert into produtos(nome,preco,descricao,quantidade,fabricantes_id) values("Tablete Android", 1500.99, "Sistema operacional 14, tela de dez polegadas", 5 , 5 );

insert into produtos(nome,preco,descricao,quantidade,fabricantes_id) values("Geladeira", 5500, "Geladeira cinza de duas porta", 12 , 6 ),("iphone 14", 7000, "258 de memoria e 8 de ram", 14 , 3 ),("Ipad", 4400, "512 gb 16 ram", 15 , 3 );
```
## select

```sql
select * from produtos;

select nome, preco from produtos;

select nome, preco,quantidade from produtos where preco < 5000;

-- mostre nome e descricao somente dos produtos da apple

select nome,descricao from produtos where fabricantes_id = 2;
```
### Operadores lógicos
```sql
-- E
select nome,preco from produtos where preco <= 6000 and preco >= 2000;


select nome,preco from produtos where preco <= 6000 and preco >= 5500;

-- OU
select nome,preco from produtos where preco <= 3000 or preco >= 5500;
 
-- exiba nome e preço somente dos produtos da apple e da sansung

select nome, preco from produtos where fabricantes_id = 3 or fabricantes_id = 5;

select nome, preco from produtos where fabricante_id in(3,5);

--NAO
select nome, preco from produtos where not fabricantes_id = 8;


select nome, preco from produtos where fabricantes_id != 8;

```