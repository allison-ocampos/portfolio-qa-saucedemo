# 🚀 Projeto de Testes Manuais (Caixa-Preta) - Sauce Demo

Este repositório demonstra a aplicação prática de técnicas de design de teste de Caixa-Preta na plataforma Sauce Demo.

* **Aplicação sob Teste (AUT):** [Sauce Demo](https://www.saucedemo.com/)
* **Tipo de Teste:** Funcional, Caixa-Preta, Manual (Front-end)

---

## 🔐 Módulo 01: Autenticação / Login

| ID | Caso de Teste | Pré-condição / Dados | Passos (Steps) | Resultado Esperado |
| :--- | :--- | :--- | :--- | :--- |
| **TC001** | Verificar login com sucesso | **User:** `standard_user`<br>**Pass:** `secret_sauce` | 1. Abrir a tela de Login<br>2. Preencher Username<br>3. Preencher Password<br>4. Clicar em "Login" | Usuário é autenticado com sucesso e redirecionado para a tela inicial de produtos (`/inventory.html`). |
| **TC002** | Login com usuário incorreto | **User:** `usuario_invalido`<br>**Pass:** `secret_sauce` | 1. Abrir a tela de Login<br>2. Preencher Username inválido<br>3. Preencher Password<br>4. Clicar em "Login" | Login é negado. Exibe o erro: `"Epic sadface: Username and password do not match any user in this service"`. |
| **TC003** | Login com usuário bloqueado | **User:** `locked_out_user`<br>**Pass:** `secret_sauce` | 1. Abrir a tela de Login<br>2. Preencher Username bloqueado<br>3. Preencher Password<br>4. Clicar em "Login" | Login é negado. Exibe o erro: `"Epic sadface: Sorry, this user has been locked out."`. |
| **TC004** | Login com campos vazios | **User:** *(vazio)*<br>**Pass:** *(vazio)* | 1. Abrir a tela de Login<br>2. Deixar campos vazios<br>3. Clicar em "Login" | Login é negado. Exibe o erro: `"Epic sadface: Username is required"`. |

---

## 🛒 Módulo 02: Carrinho de Compras

| ID | Caso de Teste | Pré-condição / Dados | Passos (Steps) | Resultado Esperado |
| :--- | :--- | :--- | :--- | :--- |
| **TC005** | Adicionar produto ao carrinho | Usuário deve estar logado no sistema. | 1. Acessar a tela de produtos<br>2. Escolher um produto da lista<br>3. Clicar no botão "Add to cart" | O botão muda o texto para `"Remove"`. O ícone do carrinho no menu superior passa a exibir o número `"1"`. |
| **TC006** | Remover produto do carrinho | Usuário logado e com produto no carrinho. | 1. Na tela de produtos<br>2. Identificar produto com botão "Remove"<br>3. Clicar no botão "Remove" | O produto é retirado do carrinho, o botão volta a exibir `"Add to cart"` e o número `"1"` desaparece do ícone. |

---

## 💳 Módulo 03: Checkout (Finalização)

| ID | Caso de Teste | Pré-condição / Dados | Passos (Steps) | Resultado Esperado |
| :--- | :--- | :--- | :--- | :--- |
| **TC007** | Finalização de compra com sucesso | Usuário logado e com produto no carrinho.<br>**Dados:** Pedro Ferreira, 2760-500 | 1. Clicar no ícone do carrinho<br>2. Clicar em "Checkout"<br>3. Preencher First Name, Last Name e Zip Code<br>4. Clicar em "Continue" | O sistema valida os dados e avança para a página de resumo de taxas (`/checkout-step-two.html`). |
| **TC008** | Checkout com campos vazios | Usuário logado e com produto no carrinho.<br>**Dados:** First Name em branco. | 1. Clicar no ícone do carrinho<br>2. Clicar em "Checkout"<br>3. Deixar "First Name" vazio<br>4. Preencher restantes e clicar em "Continue" | O sistema bloqueia o avanço e exibe o erro: `"Error: First Name is required"`. |
