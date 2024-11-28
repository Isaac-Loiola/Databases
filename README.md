# Database escola

create table instrutor(
idinstrutor int not null auto_increment,
nome varchar(50) not null,
rg int not null,
nascimento date null,
titulacao varchar(70) null,
primary key (idinstrutor)
);

create table telefoneinstrutor(
idtelefone int not null auto_increment,
telefone varchar(11) not null,
tipo varchar(15) null,
idinstrutor int not null,
primary key (idtelefone),
foreign key (idinstrutor) references instrutor(idinstrutor)
);

create table atividade(
idatividade int not null auto_increment,
nome VARCHAR(100) not null,
descricao text,
primary key (idatividade)
);

create table turma(
idturma int not null auto_increment,
horario time not null,
duracao int not null,
datainicio date not null,
datafim date not null,
idinstrutor int not null,
PRIMARY KEY (idturma),
foreign key (idinstrutor) references instrutor(idinstrutor)
);

create table aluno(
idaluno int not null auto_increment,
nome varchar(45) not null,
datanascimento date null,
altura float null,
peso int null,
primary key (idaluno)
);

create table matricula(
idaluno int not null,
idturma int not null,
foreign key (idaluno) references aluno(idaluno),
foreign key (idturma) references turma(idturma)
);

create table chamada(
idchamada int auto_increment,
data date not null,
presente tinyint not null,
idaluno int not null,
idturma int not null,
primary key (idchamada),
foreign key (idaluno) references aluno(idaluno),
foreign key (idturma) references turma(idturma)
);

create table atividade_turma (
id int auto_increment,
id_atividade int,
id_turma int,
primary key (id),
foreign key (id_atividade) references atividade(idatividade),
foreign key (id_turma) references turma(idturma)
);

desc instrutor;
desc telefoneinstrutor;
desc atividade;
desc turma;
desc aluno;
desc matricula;
desc chamada;
