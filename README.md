# Sistema de Gestão de Funko Pops  
Aplicação simples desenvolvida em **Java (Swing)** com integração ao banco de dados **MySQL**, permitindo gerenciar usuários e coleções de Funkos.

Este sistema possui telas de **login**, **cadastro de usuários**, **dashboard**, **cadastro de funkos**, **listagem de funkos** e **edição de usuário**, utilizando `CardLayout` para navegação entre telas.

---

## Tecnologias Utilizadas

- **Java 8+**
- **Swing** (Interface gráfica)
- **JDBC** (Conexão com MySQL)
- **MySQL 5.7+ / 8+**
- **NetBeans / IntelliJ / Eclipse** (qualquer IDE compatível)

---

## Funcionalidades do Sistema

### **Usuário**
- Login com email e senha  
- Cadastro de novo usuário  
- Edição dos dados do usuário logado  

### **Funkos**
- Cadastro de Funko Pop  
- Listagem de Funkos cadastrados pelo usuário logado  

### **Navegação**
Utiliza `CardLayout` para alternar entre telas:
- Tela de Login  
- Cadastro de Usuário  
- Dashboard  
- Cadastro de Funko  
- Listagem de Funkos  
- Edição de Usuário  

---

## Estrutura das Telas (Descrição Geral)

### **1. Tela de Login**
- Campos: Email e Senha  
- Botões: Entrar, Cadastrar-se  
- Valida o usuário no banco com `SELECT`  

### **2. Tela de Cadastro de Usuário**
Campos:
- Nome  
- Email  
- Senha  
- Data de Nascimento  
- Telefone  

Salva no banco via `INSERT INTO usuarios`.

### **3. Dashboard**
Opções:
- Editar Usuário  
- Cadastrar Funko  
- Listar Funkos  
- Sair  

### **4. Tela de Cadastro de Funko**
Campos:
- Nome Funko  
- Personagem  
- Número  
- Linha  
- Descrição  
- Data de Aquisição  

Salva no banco via `INSERT INTO funkos`.

### **5. Tela de Listagem de Funkos**
- Exibe todos os Funkos do usuário logado  
- Usa `SELECT` com `usuario_id`  
- Exibe resultado em `JTextArea`  

### **6. Tela de Edição de Usuário**
- Permite atualizar: Nome, Email, Telefone e Senha  
- Através de um `UPDATE usuarios SET ...`  

---

Instalação do MySQL e XAMPP

Para que o sistema funcione corretamente, é necessário ter um servidor MySQL rodando localmente. A forma mais simples é utilizando o XAMPP, que já vem com o MySQL (MariaDB) integrado.

1. Instalar o XAMPP

Acesse o site oficial: https://www.apachefriends.org

Baixe a versão mais recente para Windows.

Execute o instalador e finalize a instalação mantendo as configurações padrão.

2. Iniciar o MySQL pelo XAMPP

Abra o XAMPP Control Panel.

Clique em Start no módulo MySQL.

Quando ficar verde, o servidor já está ativo e pronto para ser usado.

3. Acessar o phpMyAdmin

Com o MySQL iniciado, clique no botão Admin ao lado de MySQL
— isso abre o phpMyAdmin no navegador.

No phpMyAdmin, crie o banco de dados conforme abaixo;

## Banco de Dados (MySQL)

### Exemplo de criação das tabelas:

```sql
create database a3;
use a3;

CREATE TABLE usuarios (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100),
    email VARCHAR(100) UNIQUE,
    senha VARCHAR(100),
    data_nascimento VARCHAR(20),
    telefone VARCHAR(20)
);

CREATE TABLE funkos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    usuario_id INT,
    nome_funko VARCHAR(100),
    personagem VARCHAR(100),
    numero VARCHAR(20),
    linha VARCHAR(100),
    descricao VARCHAR(255),
    data_aquisicao VARCHAR(20),
    FOREIGN KEY (usuario_id) REFERENCES usuarios(id)
);

