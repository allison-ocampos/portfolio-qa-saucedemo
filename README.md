# 🚀 Projeto de Testes Manuais (Caixa-Preta) - Sauce Demo

Este repositório foi desenvolvido para demonstrar habilidades técnicas na área de Garantia de Qualidade (QA), com foco em testes funcionais de interface (UI) utilizando técnicas de design de teste de Caixa-Preta.

---

## 💻 Informações do Projeto

* **Aplicação sob Teste (AUT):** [Sauce Demo](https://www.saucedemo.com/)
* **URL do Ambiente:** `https://www.saucedemo.com/`
* **Tipo de Teste:** Funcional, Caixa-Preta, Manual (Front-end)
* **Objetivo:** Validar as regras de negócio e a experiência do usuário nos fluxos críticos de Autenticação, Gerenciamento de Carrinho e Checkout de ponta a ponta.

---

## 🛠️ Pré-requisitos de Ambiente (Como Executar)

Para executar estes casos de teste, o analista precisa apenas de:
1. Um navegador web atualizado (Google Chrome, Mozilla Firefox, Edge ou Safari).
2. Acesso à internet para carregar a URL do ambiente.
3. Utilizar as credenciais válidas fornecidas no próprio site (ex: `standard_user` / `secret_sauce`).

---

## 📌 Cenários de Teste Mapeados

### 🔐 Módulo 01: Autenticação / Login

#### TC001 - Verificar login com sucesso
* **Dados de entrada:**
  * Username: `standard_user`
  * Password: `secret_sauce`
* **Steps:**
  1. Abrir a tela de Login (`https://www.saucedemo.com/`)
  2. Preencher o campo "Username" com "standard_user"
  3. Preencher o campo "Password" com "secret_sauce"
  4. Clicar no botão "Login"
* **Resultado esperado:**
  * Usuário é autenticado com sucesso e redirecionado para a tela inicial de produtos (`/inventory.html`).

#### TC002 - Verificar tentativa de login com usuário incorreto
* **Dados de entrada:**
  * Username: `usuario_invalido`
  * Password: `secret_sauce`
* **Steps:**
  1. Abrir a tela de Login
  2. Preencher o campo "Username" com "usuario_invalido"
  3. Preencher o campo "Password" com "secret_sauce"
  4. Clicar no botão "Login"
* **Resultado esperado:**
  * Login é negado e o sistema exibe a mensagem de erro: `"Epic sadface: Username and password do not match any user in this service"`.

#### TC003 - Verificar tentativa de login com usuário bloqueado
* **Dados de entrada:**
  * Username: `locked_out_user`
  * Password: `secret_sauce`
* **Steps:**
  1. Abrir a tela de Login
  2. Preencher o campo "Username" com "locked_out_user"
  3. Preencher o campo "Password" com "secret_sauce"
  4. Clicar no botão "Login"
* **Resultado esperado:**
  * Login é negado e o sistema exibe a mensagem de erro: `"Epic sadface: Sorry, this user has been locked out."`.

#### TC004 - Verificar tentativa de login com campos vazios
* **Dados de entrada:**
  * Username: *(vazio)*
  * Password: *(vazio)*
* **Steps:**
  1. Abrir a tela de Login
  2. Manter o campo "Username" vazio
  3. Manter o campo "Password" vazio
  4. Clicar no botão "Login"
* **Resultado esperado:**
  * Login é negado e o sistema exibe a mensagem de erro: `"Epic sadface: Username is required"`.

---

### 🛒 Módulo 02: Carrinho de Compras

#### TC005 - Verificar a adição de produtos no carrinho de compras
* **Pré-condição:** O usuário deve estar logado no sistema.
* **Steps:**
  1. Abrir a tela inicial de produtos do sistema
  2. Escolher um produto da lista
  3. Clicar no botão "Add to cart"
* **Resultado esperado:**
  * O botão do produto selecionado muda o texto para `"Remove"`.
  * O ícone do carrinho de compras (superior direito) passa a exibir o número `"1"`.
  * O usuário permanece na tela de produtos.

#### TC006 - Verificar fluxo de remover produtos do carrinho de compras
* **Pré-condição:** O usuário deve estar logado no sistema e possuir um produto adicionado ao carrinho.
* **Steps:**
  1. Na tela inicial de produtos
  2. Localizar o produto que está com o botão exibindo "Remove"
  3. Clicar no botão "Remove"
* **Resultado esperado:**
  * O produto é retirado do carrinho, o botão volta a exibir `"Add to cart"` e o número `"1"` desaparece do ícone do carrinho.

---

### 💳 Módulo 03: Checkout (Finalização de Compra)

#### TC007 - Verificar finalização de compras no Checkout
* **Pré-condição:** O usuário deve estar logado no sistema e com produto adicionado ao carrinho.
* **Dados de entrada:**
  * First Name: `Pedro`
  * Last Name: `Ferreira`
  * Zip/Postal Code: `2760-500`
* **Steps:**
  1. Na tela inicial de produtos, clicar no ícone do carrinho de compras
  2. Clicar no botão "Checkout"
  3. Preencher o campo "First Name" com "Pedro"
  4. Preencher o campo "Last Name" com "Ferreira"
  5. Preencher o campo "Zip/Postal Code" com "2760-500"
  6. Clicar no botão "Continue"
* **Resultado esperado:**
  * O sistema valida os dados e redireciona o usuário para a página de visão geral e resumo de taxas (`/checkout-step-two.html`).

#### TC008 - Verificar tentativa de Checkout com campos obrigatórios vazios
* **Pré-condição:** O usuário deve estar logado no sistema e com produto adicionado ao carrinho.
* **Dados de entrada:**
  * Last Name: `Ferreira`
  * Zip/Postal Code: `2760-500`
* **Steps:**
  1. Na tela inicial de produtos, clicar no ícone do carrinho de compras
  2. Clicar no botão "Checkout"
  3. Manter o campo "First Name" vazio
  4. Preencher o campo "Last Name" com "Ferreira"
  5. Preencher o campo "Zip/Postal Code" com "2760-500"
  6. Clicar no botão "Continue"
* **Resultado esperado:**
  * O sistema bloqueia o avanço e exibe a mensagem de erro: `"Error: First Name is required"`.
