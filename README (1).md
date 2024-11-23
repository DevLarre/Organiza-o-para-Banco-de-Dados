
# 🌟 Sistema de Banco de Dados para Novo Airbnb 🌟

Este projeto descreve como organizar o banco de dados inicial para um sistema similar ao Airbnb. O objetivo é atender aos requisitos de gerenciamento de usuários, lugares, hospedagens e avaliações.

## 📋 Descrição do Projeto

O banco de dados é modelado para permitir que:
- Usuários se cadastrem e gerenciem suas contas.
- Lugares para hospedagem sejam cadastrados pelos usuários.
- Hospedagens sejam criadas, indicando as reservas feitas por usuários.
- Avaliações sejam realizadas pelos hóspedes após estadias.

## 🛠️ Estrutura do Banco de Dados

### 🔑 **Tabelas e Colunas**
1. **`usuarios`**
   - `id_usuario` (INT, PK): Identificador único do usuário.
   - `nome` (VARCHAR): Nome do usuário.
   - `email` (VARCHAR): E-mail para login.
   - `senha` (VARCHAR): Senha do usuário.
   - `data_criacao` (DATETIME): Data de criação do perfil.

2. **`lugares`**
   - `id_lugar` (INT, PK): Identificador único do lugar.
   - `nome` (VARCHAR): Nome do lugar.
   - `localizacao` (VARCHAR): Endereço ou coordenadas do lugar.
   - `descricao` (TEXT): Detalhes do lugar.
   - `id_usuario` (INT, FK): Relacionamento com o proprietário (`usuarios.id_usuario`).

3. **`hospedagens`**
   - `id_hospedagem` (INT, PK): Identificador único da hospedagem.
   - `id_usuario` (INT, FK): Relacionamento com o hóspede (`usuarios.id_usuario`).
   - `id_lugar` (INT, FK): Relacionamento com o lugar reservado (`lugares.id_lugar`).
   - `data_inicio` (DATETIME): Data de início da hospedagem.
   - `data_fim` (DATETIME): Data de término da hospedagem.

4. **`avaliacoes`**
   - `id_avaliacao` (INT, PK): Identificador único da avaliação.
   - `id_usuario` (INT, FK): Relacionamento com quem avaliou (`usuarios.id_usuario`).
   - `id_lugar` (INT, FK): Relacionamento com o lugar avaliado (`lugares.id_lugar`).
   - `nota` (INT): Nota de 1 a 5 atribuída pelo hóspede.
   - `comentario` (TEXT): Comentário descritivo da experiência.

---

### 🔗 **Relacionamentos**
- **`usuarios` ↔ `lugares`**: Um usuário pode cadastrar vários lugares, mas um lugar pertence a um único usuário.
- **`usuarios` ↔ `hospedagens`**: Um usuário pode reservar vários lugares (hóspede).
- **`lugares` ↔ `hospedagens`**: Um lugar pode ter várias reservas (hospedagens).
- **`usuarios` ↔ `avaliacoes`**: Um usuário pode fazer várias avaliações.
- **`lugares` ↔ `avaliacoes`**: Um lugar pode receber várias avaliações.

---

## 📂 Estrutura do Projeto

- **Diagramas:** Inclua o diagrama ER para visualização (não incluso neste README).
- **SQL:** O script de criação do banco pode ser encontrado no repositório do GitHub.

---

## 🚀 Como Acessar

1. Clone este repositório:
   ```bash
   git clone <URL_DO_REPOSITORIO>
   ```
2. Navegue para o diretório e acesse o arquivo do banco:
   ```bash
   cd nome-do-projeto
   ```

3. Execute o script SQL para criar o banco:
   ```bash
   mysql -u usuario -p < script.sql
   ```

---

## ✨ Decisões de Design

- A escolha de tabelas normalizadas garante consistência e evita duplicação de dados.
- IDs são usados para garantir a unicidade de cada registro e facilitar os relacionamentos.
- As colunas e os relacionamentos foram definidos para cobrir todas as interações do sistema.

---

Feito com ❤️ para ajudar você a criar um banco de dados funcional e escalável!
