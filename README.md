# 🚀 Projeto de Testes Manuais - Sauce Demo

Este repositório demonstra a aplicação prática de técnicas de design de teste de Caixa-Preta na plataforma Sauce Demo.

* **Aplicação sob Teste (AUT):** [Sauce Demo](https://www.saucedemo.com/)
* **Tipo de Teste:** Funcional, Caixa-Preta, Manual (Front-end)

---

## 🔐 Módulo 01: Autenticação / Login

### 📊 Matriz de Cenários
| ID | Caso de Teste | Tipo de Teste | Resultado Esperado |
| :--- | :--- | :--- | :--- |
| **TC001** | Login com sucesso | Positivo | Usuário autenticado e redirecionado para `/inventory.html` |
| **TC002** | Login com usuário incorreto | Negativo | Bloqueio e mensagem: `Username and password do not match...` |
| **TC003** | Login com usuário bloqueado | Negativo | Bloqueio e mensagem: `Sorry, this user has been locked out.` |
| **TC004** | Login com campos vazios | Negativo | Bloqueio e mensagem: `Username is required` |

### 📝 Detalhamento dos Passos

#### **TC001 - Login com sucesso**
* **Dados de entrada:** `standard_user` / `secret_sauce`
* **Passos:**
  1. Acessar a página de login do Sauce Demo.
  2. Preencher o campo "Username" com um usuário válido.
  3. Preencher o campo "Password" com a senha correspondente.
  4. Clicar no botão "Login".

#### **TC002 - Login com usuário incorreto**
* **Dados de entrada:** `usuario_invalido` / `secret_sauce`
* **Passos:**
  1. Acessar a página de login.
  2. Preencher o campo "Username" com um valor inexistente.
  3. Preencher o campo "Password" com uma senha qualquer.
  4. Clicar no botão "Login".

#### **TC003 - Login com usuário bloqueado**
* **Dados de entrada:** `locked_out_user` / `secret_sauce`
* **Passos:**
  1. Acessar a página de login.
  2. Preencher o campo "Username" com o usuário bloqueado pelo sistema.
  3. Preencher o campo "Password" com a senha correspondente.
  4. Clicar no botão "Login".

#### **TC004 - Login com campos vazios**
* **Dados de entrada:** Ambos os campos em branco.
* **Passos:**
  1. Acessar a página de login.
  2. Manter os campos de credenciais totalmente limpos.
  3. Clicar no botão "Login".

---

## 🛒 Módulo 02: Carrinho de Compras

### 📊 Matriz de Cenários
| ID | Caso de Teste | Pré-condição | Resultado Esperado |
| :--- | :--- | :--- | :--- |
| **TC005** | Adicionar produto ao carrinho | Usuário logado | Botão muda para `Remove` e o contador do carrinho exibe `1` |
| **TC006** | Remover produto do carrinho | Produto no carrinho | Botão volta para `Add to cart` e o contador do carrinho zera |

### 📝 Detalhamento dos Passos

#### **TC005 - Adicionar produto ao carrinho**
* **Passos:**
  1. Na vitrine de produtos, escolher um item de preferência.
  2. Clicar no botão "Add to cart" do produto escolhido.
  3. Validar a alteração do texto do botão e do ícone do carrinho.

#### **TC006 - Remover produto do carrinho**
* **Passos:**
  1. Na vitrine de produtos, identificar o item que já foi adicionado.
  2. Clicar no botão "Remove" deste produto.
  3. Validar se o item foi subtraído do contador do carrinho.

---

## 💳 Módulo 03: Checkout (Finalização)

### 📊 Matriz de Cenários
| ID | Caso de Teste | Dados de Entrada | Resultado Esperado |
| :--- | :--- | :--- | :--- |
| **TC007** | Checkout com sucesso | Pedro, Ferreira, 2760-500 | Redirecionamento para a página de resumo (`/checkout-step-two.html`) |
| **TC008** | Checkout com "First Name" vazio | Ferreira, 2760-500 | Bloqueio e mensagem: `Error: First Name is required` |

### 📝 Detalhamento dos Passos

#### **TC007 - Checkout com sucesso**
* **Pré-condição:** Usuário logado e com pelo menos um item no carrinho.
* **Passos:**
  1. Clicar no ícone do carrinho de compras e avançar clicando em "Checkout".
  2. Preencher todos os campos obrigatórios (Nome, Sobrenome e CEP).
  3. Clicar no botão "Continue".

#### **TC008 - Checkout com campos vazios**
* **Pré-condição:** Usuário logado e com pelo menos um item no carrinho.
* **Passos:**
  1. Clicar no ícone do carrinho de compras e avançar clicando em "Checkout".
  2. Deixar o campo "First Name" em branco.
  3. Preencher os campos "Last Name" e "Zip/Postal Code".
  4. Clicar no botão "Continue".
