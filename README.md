# trabalhoLuiz
# -Inventário Minecraft

## 1. Introdução

### a. Qual o objetivo da atividade?
O objetivo desta atividade é desenvolver um sistema de inventário para um jogo, implementando funcionalidades de login, exibição e manipulação de itens.

#### i. O que é um inventário em um jogo? Qual a finalidade? Dê exemplos.
Um inventário em um jogo é um sistema que permite ao jogador armazenar, visualizar e gerenciar itens adquiridos ao longo do jogo. Ele pode incluir armas, ferramentas, recursos e objetos colecionáveis. Exemplos de jogos com inventários incluem *Minecraft*, *The Legend of Zelda* e *Skyrim*.

#### ii. Que tipos de sistemas utilizam essa funcionalidade? Dê exemplos.
Além de jogos eletrônicos, sistemas como lojas virtuais, aplicações de gerenciamento de estoque e plataformas de e-commerce também utilizam funcionalidades de inventário. Exemplos incluem Amazon, Mercado Livre e sistemas de ERP.

#### iii. Porque essa funcionalidade é importante?
A funcionalidade de inventário é essencial para organizar e gerenciar itens dentro de um sistema, seja em um jogo ou em uma aplicação real. Ela melhora a experiência do usuário e otimiza a administração de recursos.

---

## 2. A Implementação

### a. Front-end

#### i. Quais ferramentas foram utilizadas (editores/linguagens)? Por quê? O que cada um deles faz?
- **HTML**: Estrutura do site.
- **CSS**: Estilização da interface.
- **PHP**: Lógica do servidor e autenticação de usuários.

O código foi desenvolvido em um editor de texto (VS Code), que oferece suporte para várias linguagens e facilita a edição do projeto.

#### ii. Como o layout foi definido? Como a interface foi setorizada? Relação linhas x colunas.
O layout foi inspirado no inventário do jogo *Minecraft*, organizando os itens em um formato de grade. Cada item ocupa um espaço fixo e tem uma imagem representativa.

### b. Back-end

#### i. Quais ferramentas foram utilizadas (editores/linguagens)? Por quê? O que cada um deles faz?
- **PHP**: Gerenciamento de sessão, autenticação de usuários e controle do inventário.
- **Sessions**: Para manter o estado do usuário logado.

#### ii. Sobre o código PHP

##### 1. O que o código faz? Explicar as principais funcionalidades com exemplos de código.

- **`login.php`**: Verifica as credenciais do usuário e inicia a sessão.
  - O login utiliza o método **POST** para enviar os dados de login de forma segura, sem exibi-los na URL.
```php
session_start();
if ($_SERVER['REQUEST_METHOD'] == 'POST') {
    if ($_POST['username'] == 'Duda' && $_POST['password'] == 'dudaakz') {
        $_SESSION['user'] = 'Duda';
        header('Location: inventario.php');
    } else {
        echo "Usuário ou senha incorretos.";
    }
}
```

- **`logout.php`**: Destroi a sessão e redireciona para a página de login.
```php
session_start();
session_destroy();
header('Location: login.php');
```

- **`inicio.php`**: Exibe os itens do inventário em uma grade semelhante ao *Minecraft*.
```php
<?php
session_start();
if (!isset($_SESSION['user'])) {
    header('Location: login.php');
    exit();
}
?>
<!DOCTYPE html>
<html>
<head>
    <title>Inventário</title>
    <link rel="stylesheet" type="text/css" href="styles.css">
</head>
<body>
    <h1>Bem-vindo ao Inventário</h1>
    <div class="inventory-grid">
        <div class="item">Pedra</div>
        <div class="item">Madeira</div>
        <div class="item">Ferro</div>
    </div>
    <a href="logout.php">Sair</a>
</body>
</html>
```

**Prints incluídos:**
- Tela de login utilizando método **POST**.
- Código da página `inicio.php`.
- Prints do sistema rodando, mostrando o inventário funcionando corretamente.

---

## 3. Passo a passo de execução

### a. Explicar o que deve ser feito para executar o projeto
1. Subir os arquivos do projeto para um servidor local(xampp)
2. Acessar `http://localhost/trabalhoLuiz/login.php`.
3. Fazer login com as credenciais (`Duda` / `dudaakz`).
4. Navegar pelo inventário após o login.

### b. Explicar a hierarquia de diretórios do projeto
```
trabalhoLuiz/
│-- index.php
│-- login.php
│-- logout.php
│-- inventario.php
│-- assets/
│   ├── css/
│   ├── imagens/
│-- includes/
│-- prints/
│   ├── login_post.png
│   ├── inicio_codigo.png
│   ├── sistema_rodando1.png
│   ├── sistema_rodando2.png
```
A pasta `assets/` contém os arquivos de estilo e imagens. A pasta `includes/` pode conter códigos reutilizáveis, como conexões com banco de dados. A pasta `prints/` contém as capturas de tela do desenvolvimento e execução do projeto.


