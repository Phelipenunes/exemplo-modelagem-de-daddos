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

select nome, preco from produtos where fabricante_id not in(3,5);

--NAO
select nome, preco from produtos where not fabricantes_id = 8;

select nome, preco from produtos where fabricante_id not in(3,5);

select nome, preco from produtos where fabricantes_id != 8;

-- Outras formas de uso

select nome,preco from produtos order by nome; 

select nome,preco from produtos order by preco desc;

```

## UPDATE
```sql
update fabricantes set nome = 'asus do brasil' where id = 1;

update produtos set preco = 3500 where id = 1;


-- altere aquantidade dos produtos da apple e da sansung para 20
update produtos set quantidade = 20 where fabricantes_id = 3 or fabricantes_id = 5;
```

## DELETE
```sql

delete from fabricantes where id = 1

```
### Opereções com funções  
```sql

select SUM(preco) from produtos;

select SUM(preco)as total from produtos;


select nome as produtos,preco as "preço" from produtos;


select avg(preco) as "Média dos preços" from produtos;

select round(avg(preco),2) as "Média dos preços" from produtos;

select count(id) as "quantidade de preços" from produtos;

select count(fabricantes_id) as "quantidade de fabricante" from produtos;

select count(distinct fabricantes_id) as "quantidade de fabricante" from produtos;

select nome,preco,quantidade,(preco * quantidade) from produtos;

select sum(preco) from produtos;

```
## Consultas (queries) em duas ou mais tabelas relacionadas (JUNÇÃO/JOIN)
### Exibir nome dos produtos com nome dos fabricantes

```sql

select produtos.nome as produtos,fabricantes.nome as fabricantes from produtos inner join fabricantes  on produtos.fabricantes_id = fabricantes.id;

```
### noem do produto, nome do fabricante, ordenados pelo nome do produto

```sql

select produtos.nome as produtos,produtos.preco,fabricantes.nome as fabricantes from produtos inner join fabricantes on produtos.fabricantes_id = fabricantes.id order by produtos; 
```

### fabricantes, soma dos preços e a quantidade de produtos
```sql
select fabricantes.nome as fabricantes,
sum(produtos.preco) as total, count(produtos.fabricante_id) as "qtd de produtos"
from produtos inner join fabricantes
on produtos.fabricantes_id = fabricantes.id
group by fabricantes order by total

```

### traga a quantidade de produtos de cada fabricantes
```sql

--traga a quantidade de produtos de cada fabricantes e a soma somente dos fabricantes que possuem produtos
select fabricantes.nome as fabricante,
sum(produtos.quantidade) as "qtd estoque",
count(produtos.fabricantes_id) as "qtd de produtos"
from produtos inner join fabricantes on produtos.fabricantes_id = fabricantes.id
group by fabricante


--traga a quantidade de produtos de cada fabricantes e a soma somente dos fabricantes que possuem produtos com os que nao possuem produtos 
select fabricantes.nome as fabricante,
sum(produtos.quantidade) as "qtd estoque",
count(produtos.fabricantes_id) as "qtd de produtos"
from produtos right join fabricantes on produtos.fabricantes_id = fabricantes.id
group by fabricante


```