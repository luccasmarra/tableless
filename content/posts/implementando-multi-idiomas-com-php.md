---
title: Implementando Multi-idiomas com PHP
authors: Luccas Marra do Amaral
type: post
date: 2018-12-14
excerpt: Como tornar sua aplicação Web em multi-idiomas com PHP.
categories:
  - Front-end
  - Back-end
  - HTML
tags:
  - Aplicação Web Multi-idiomas com PHP
  - Website tradução de idiomas
---


# Implementando Multi-idiomas com PHP 


Não é de hoje que a internet quebrou as barreiras da comunicação e é um dos maiores fatores decisivos quando queremos comprar, vender, ter entretenimento, empreender, aumentar nosso conhecimento, conhecer pessoas/lugares e realizar negócios. Levando em consideração que no mundo temos mais de 190 países, imagine quantos internautas com idiomas diferentes podemos nos comunicar.
Neste artigos vamos utilizar um cenário muito bem recorrente. Diversos sistemas web e websites são desenvolvidos pensando somente em um único idioma e isso impossibilita que usuários estrangeiros possam navegar de maneira confortável, por isso acabam desistindo da navegação e muitas vezes interesse pelo assunto. Mas isso tem uma solução e abaixo mostrarei como ter diversos idiomas em sua aplicação PHP de forma organizada e sem a necessidade de banco de dados.


Abaixo você encontrará 5 etapas didáticas para você implementar o multi-idiomas a sua aplicação PHP.
 

### 1 - Organização dos arquivos

Crie uma pasta “traducoes” na raiz do seu projeto e os seguintes arquivos dentro dela: 

* tradutor.php
* pt-br.php
* en-us.php

```Caso queira mais idiomas você poderá criar seguindo a mesma organização.```

  

### 2 - Alimentando nossos arquivos de tradução
Ambos devem conter as mesmas variáveis para que o nosso script PHP que sera criado entenda e designe os dados corretamente. O conteúdo de cada idioma seguirá a mesama estrutura porém com conteúdos serão diferentes, como no exemplo abaixo:


**Conteúdo arquivo**: `pt-br.php` 

```
<?php 
// Traduções em Português
$trad[‘titulo’] = ‘Olá, bem vindo’;
$trad[‘texto’] = ‘Neste momento estamos utilizando a versão em Português’;
?>
```

**Conteúdo arquivo**: `en-us.php` 

```
<?php 
// Traduções em Inglês
$trad[‘titulo’] = ‘Hello, Welcome’;
$trad[‘texto’] = ‘At this moment we are using a English version’];
?>
```


### 3 - Criando a lógica em PHP para controle de idioma na $_SESSION

Repare que na etapa anterior os dois arquivos possuem as mesmas variáveis porem com conteúdos de acordo com seu respectivo idioma. Agora, vamos criar o nosso script PHP que controlará qual idioma será exibido.
 
**Conteúdo arquivo**: `tradutor.php` 

```
<?php
// Inicia uma sessão (* sempre no topo da pagina)
session_start();

// Define qual idioma será utilizado
if(!isset($_SESSION['idioma']){
    // Define um idioma inicial
    $_SESSION['idioma'] = 'pt-bt.php';
    
// Define um novo idioma a partir de um get
}else if(isset($_GET['idioma'])){
    include 'traducoes/'.$_GET['idioma'].'.php';
};?>

```


### 4 - Como Alterar o Idioma

Utilize o método GET para alterar o seu idioma, isso é feito de maneira simples através de um link comum apontado para sua própria pagina, como o exemplo abaixo:

```
<a href="?idioma=pt-br.php">Português</a>
<a href="?idioma=en-us.php">Inglês</a>
```


### 4 - Finalizando e testando nossa implementação

Agora basta você incluir no topo de sua pagina PHP o codigo que sera responsável por controlar o idioma que os usuários poderão navegar.

```
<?php include('tradutor.php');?>
```

E por final, seu codigo (PHP/HTML) ficará parecido com o abaixo:

```
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8"/>
		<title><?php echo $trad[‘titulo’];?></title>
	</head>
	
	<body>
		<?php echo $trad[aviso];?>
	</body>
</html>
```
