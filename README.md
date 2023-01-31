This is the README WT2

CREATE BASIC DB:


DROP TABLE IF EXISTS members;
CREATE TABLE members (
	id SERIAL PRIMARY KEY,
	meno varchar(255),
	priezvisko varchar(255),
	vek int,
	pribuzenstvo varchar(255)
	
);


INSERT INTO members (meno,priezvisko,vek,pribuzenstvo)
VALUES 
('Patrik','Mrkvička',21,'ja'),
('Markus','Mrkvička',15,'brat'),
('Max','Mrkvička',31,'ujo'),
('Katarina','Mrkvičková',40,'mama'),
('Dominik','Mrkvička',43,'otec')
;

// pozor na schemu, tabulka members musi byt v scheme public kvoli funkcii getSize()


1) Node

Ako prvé budeme potrebovať node.js.
Odporučaná (moja) verzia je v14.17.0.
Dostupná na: https://nodejs.org/download/release/v14.17.0/

2) PostgreSQL
Ďalej je potrebné nainštalovať DB.
Odporučaná (moja) verzia je PostgreSQL 12.9, compiled by Visual C++ 1914, 64-bit.
Dostupné na: https://www.enterprisedb.com/postgresql-tutorial-resources-training?uuid=03b13357-9281-4985-baea-17b72a0febc3&campaignId=7012J000001F5IIQA0

prípadne: https://www.enterprisedb.com/downloads/postgres-postgresql-downloads

3) Po inštalácii Node a PostgreSQL je potrebné podstúpiť niekoľko inicializačných krokov

Po inštalácii PostgreSQL by sme mali mať "pgAdmin 4" spustiteľný súbor k dispozícii.
Windows -> štart -> hľadať -> "pgAdmin"

Spustíme tento program, ako prvé je potrebné zvoliť username,heslo a pod. k našej DB.
Postupujme podľa obrázkov:
#OBR#
meno, heslo, port a pod. by malo byť rovnaké ako sú parametre v súbore webtech/WT_2/.env

Následne vytvoríme a naplnime tabuľku, kt. budeme používať v našej webovej app.
(pre jednoduchosť skopírujme nasledujuci kód, viď. obr.) 


`
CREATE BASIC DB:


DROP TABLE IF EXISTS members;
CREATE TABLE members (
	id SERIAL PRIMARY KEY,
	meno varchar(255),
	priezvisko varchar(255),
	vek int,
	pribuzenstvo varchar(255)
	
);


INSERT INTO members (meno,priezvisko,vek,pribuzenstvo)
VALUES 
('Patrik','Mrkvička',21,'ja'),
('Markus','Mrkvička',15,'brat'),
('Max','Mrkvička',31,'ujo'),
('Katarina','Mrkvičková',40,'mama'),
('Dominik','Mrkvička',43,'otec')
;
`

*Je potrebné tento kód vložiť do hlavného adresára Servers/PostgreSQL/postgres/Schemas/public/Tables*


4) spustenie PostgreSQL servera
PostgresSQL server sa spusta/vypina následovne:

1) win+R -> "services.msc"
2) nájdeme položku "postgresql-x64-12 - PostgreSQL Server 12"
3) pravým tlačidlom myši klikneme na túto položku a vyberieme Start/Stop (podľa toho či chceme server zapnut/vypnut)

5) Spustenie Node servera
Spustenie Node servera je podstatne jednochuchšie.

1) Vo VScode (alebo cmd/terminali) otvoríme zložku WT_2 (webtech/WT_2)
2) Do terminálu napíseme príkaz "npm start"

v terminali by sme mali dostat nieco ako
`
[nodemon] 2.0.15
[nodemon] to restart at any time, enter `rs`
[nodemon] watching path(s): *.*
[nodemon] watching extensions: js,mjs,json  
[nodemon] starting `node index.js`
Server is up and running on port 5000 ...
`

Teraz nám už len ostáva otestovať nasšu web-appku.

http://localhost:5000/
