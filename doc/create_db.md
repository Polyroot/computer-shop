# Создаем базу данных нашего магазина компьютеров
Начнем создавать нашу бд

откроем query tool для исполнения скриптов
чтобы создать базу данных
```
CREATE DATABASE computer_shop;
```
создаем нашу таблицу с продуктами которые наш онлайн магазин будет продавать
```
CREATE TABLE product
(
    maker varchar (10) NOT NULL,
    model varchar(50) NOT NULL,
    type_p varchar(50) NOT NULL,
    CONSTRAINT product_pkey PRIMARY KEY (model)
)
```
создаем таблицу где будем хранить наши ноутбуки
```
CREATE TABLE laptop
(
    code bigint NOT NULL GENERATED ALWAYS AS IDENTITY ( INCREMENT 1 START 1 MINVALUE 1 MAXVALUE 9223372036854775807 CACHE 1 ),
    model character varying(50) COLLATE NOT NULL,
    speed smallint NOT NULL,
    ram smallint NOT NULL,
    hd real NOT NULL,
    price numeric NOT NULL,
    screen smallint NOT NULL,
    CONSTRAINT laptop_pkey PRIMARY KEY (code),
    CONSTRAINT fk_laptop FOREIGN KEY (model) REFERENCES product(model)
)
```
создаём таблицу для принтеров
```
CREATE TABLE printer
(
    code bigint NOT NULL GENERATED ALWAYS AS IDENTITY ( INCREMENT 1 START 1 MINVALUE 1 MAXVALUE 9223372036854775807 CACHE 1 ),
    model character varying(50) NOT NULL,
    color character(1) NOT NULL,
    type_pri character varying(10) NOT NULL,
    price numeric NOT NULL,
    CONSTRAINT printer_pkey PRIMARY KEY (code),
    CONSTRAINT fk_printer_product FOREIGN KEY (model) REFERENCES product(model)
)
```
создаем таблицу с компьютерами
```
CREATE TABLE pc
(
    code bigint NOT NULL GENERATED ALWAYS AS IDENTITY ( INCREMENT 1 START 1 MINVALUE 1 MAXVALUE 9223372036854775807 CACHE 1 ),
    model character varying(50) COLLATE NOT NULL,
    speed smallint NOT NULL,
    ram smallint NOT NULL,
    hd real NOT NULL,
    cd character varying(10) COLLATE NOT NULL,
    price numeric NOT NULL,
    CONSTRAINT pc_pkey PRIMARY KEY (code),
    CONSTRAINT fk_pc_product FOREIGN KEY (model) REFERENCES product(model)
)
```