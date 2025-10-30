## Cenário 02: Nova Venda 

### Caso de Teste 01: Venda completa com múltiplos itens e pagamento dividido (Caminho Feliz)

| ID | Descrição |
| :------- | :----------------------------------------------------------------------------------------------------------------------------------- |
| C02-CT01 | Realizar uma venda completa, adicionando múltiplos itens (com desconto) e finalizando com pagamento dividido (Dinheiro e Cartão Crédito). |

| **Pré-condições** |
| :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| O usuário deve estar logado e na tela principal.<br>O "Cliente" desejado deve estar cadastrado.<br>O "Funcionário" ("EMPRESA") deve estar cadastrado.<br>Os produtos (ex: "1" e "2") devem estar cadastrados, com preço e estoque disponíveis. |

| **Passos** |
| :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **DADO** que o usuário clicou no ícone "Venda" e depois no botão "Novo"<br>**E** selecionou um "Cliente" e um "Funcionário" (ex: "EMPRESA")<br>**E** clicou em "Salvar" no cabeçalho<br>**E** no campo "Produto", digitou "1", pressionou Enter, inseriu "1" em "Quant." e "10,00" em "Desconto %"<br>**E** clicou em "Salvar" (item)<br>**E** clicou em "Novo" (itens), digitou "2" em "Produto", pressionou Enter, inseriu "1" em "Quant."<br>**E** clicou em "Salvar" (item)<br>**QUANDO** o usuário clicar no botão "Finalizar"<br>**E** na janela "Confirmar Venda", alterar "Status" para "CONFIRMADA" e "Condição Venda" para "A VISTA"<br>**E** na aba "Pagamento", clicar no botão "..." e selecionar "DINHEIRO"<br>**E** preencher o "Valor" (ex: "20000") e clicar em "Salvar" (pagamento)<br>**E** o campo "Diferença" mostrar o valor restante<br>**E** clicar no botão "..." novamente e selecionar "CARTÃO CRÉDITO" (valor preenchido automaticamente)<br>**E** clicar em "Salvar" (pagamento)<br>**E** a "Diferença" estiver zerada<br>**E** o usuário clicar no botão principal "Salvar" (F4)<br>**ENTÃO** a venda deve ser concluída e salva com sucesso.<br>**E** a tela de "Venda" deve ser limpa, pronta para um novo pedido. |

| **Critérios de aceitação** |
| :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| A venda deve ser registrada no sistema com o status "CONFIRMADA".<br>O estoque dos produtos "1" e "2" deve ser debitado corretamente.<br>Os dois pagamentos (DINHEIRO, CARTÃO CRÉDITO) devem estar corretamente associados à venda.<br>O desconto de 10% deve ser aplicado corretamente ao item "1". |

---

### Caso de Teste 02: Tentativa de salvar cabeçalho sem selecionar cliente (Negativo)

| ID | Descrição |
| :------- | :-------------------------------------------------------------------------------------- |
| C02-CT02 | O sistema não deve permitir salvar o cabeçalho da venda sem um cliente selecionado. |

| **Pré-condições** |
| :-------------------------------------------------- |
| O usuário está na tela de "Venda" (clicou em "Novo"). |

| **Passos** |
| :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **DADO** que o usuário clicou no ícone "Venda" e depois no botão "Novo"<br>**E** selecionou "EMPRESA" no campo "Funcionário"<br>**E** deixou o campo "Cliente" em branco<br>**QUANDO** o usuário clicar em "Salvar" (no cabeçalho)<br>**ENTÃO** o sistema deve exibir uma mensagem de validação (ex: "Campo Cliente é obrigatório").<br>**E** o foco não deve mudar para a seção "Entrada de Produtos". |

| **Critérios de aceitação** |
| :------------------------------------------------------------------------------------- |
| A validação de campo obrigatório para "Cliente" deve ser exibida.<br>O cabeçalho não deve ser salvo. |

---

### Caso de Teste 03: Tentativa de adicionar produto com código inexistente (Negativo)

| ID | Descrição |
| :------- | :------------------------------------------------------------------------------------------------------ |
| C02-CT03 | O sistema deve exibir um erro ao tentar adicionar um código de produto que não existe no cadastro. |

| **Pré-condições** |
| :--------------------------------------------------------------------------- |
| O usuário está na tela de "Venda" e já salvou o cabeçalho (Cliente/Funcionário). |

| **Passos** |
| :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **DADO** que o usuário salvou o cabeçalho da venda<br>**E** no campo "Produto", digitou um código inválido (ex: "999999") e pressionou Enter<br>**QUANDO** o sistema tentar buscar o produto<br>**ENTÃO** o sistema deve exibir uma mensagem de erro (ex: "Produto não encontrado" ou "Código inválido").<br>**E** o item não deve ser adicionado à lista e os campos (Quant, Desconto) não devem ser habilitados. |

| **Critérios de aceitação** |
| :----------------------------------------------------------------- |
| Mensagem de erro de produto inválido/inexistente deve ser exibida.<br>O grid de itens não deve ser alterado. |

---

### Caso de Teste 04: Tentativa de adicionar produto com quantidade zero (Negativo)

| ID | Descrição |
| :------- | :------------------------------------------------------------------------------------- |
| C02-CT04 | O sistema não deve permitir adicionar um produto ao pedido com quantidade igual a zero. |

| **Pré-condições** |
| :--------------------------------------------------------------------------- |
| O usuário está na tela de "Venda" e já salvou o cabeçalho (Cliente/Funcionário). |

| **Passos** |
| :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **DADO** que o usuário salvou o cabeçalho da venda<br>**E** no campo "Produto", digitou um código válido (ex: "1") e pressionou Enter<br>**E** no campo "Quant." (Quantidade), inseriu "0"<br>**QUANDO** o usuário clicar em "Salvar" (para adicionar o item)<br>**ENTÃO** o sistema deve exibir uma mensagem de validação (ex: "Quantidade deve ser maior que zero").<br>**E** o item não deve ser adicionado à lista. |

| **Critérios de aceitação** |
| :----------------------------------------------------------------- |
| Validação de quantidade mínima deve ser exibida.<br>O item não deve ser salvo no pedido. |

---

### Caso de Teste 05: Tentativa de finalizar a venda com pagamento incompleto (Negativo)

| ID | Descrição |
| :------- | :----------------------------------------------------------------------------------------------------------------------------------- |
| C02-CT05 | O sistema não deve permitir salvar a venda se o valor pago ("Valor Recebido") for menor que o total da venda ("Diferença" > 0). |

| **Pré-condições** |
| :----------------------------------------------------------------------------------------------------------------- |
| O usuário adicionou produtos (ex: Total R$ 300,00) e está na janela "Confirmar Venda" (após clicar em "Finalizar"). |

| **Passos** |
| :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **DADO** que o usuário clicou em "Finalizar" e está na janela "Confirmar Venda"<br>**E** alterou o "Status" para "CONFIRMADA"<br>**E** na aba "Pagamento", adicionou "DINHEIRO" com um valor *menor* que o total (ex: "200,00" quando o total é "300,00")<br>**E** clicou em "Salvar" (no pagamento)<br>**E** a "Diferença" ainda mostra um valor positivo (ex: "100,00")<br>**QUANDO** o usuário clicar no botão principal "Salvar" (F4)<br>**ENTÃO** o sistema deve exibir uma mensagem de erro (ex: "O valor pago é inferior ao total. Verifique a Diferença." ou "Valor restante a pagar.").<br>**E** a janela "Confirmar Venda" não deve ser fechada. |

| **Critérios de aceitação** |
| :------------------------------------------------------------------------------------------------------------- |
| A venda não deve ser salva.<br>Uma mensagem de erro clara sobre o valor pendente ("Diferença") deve ser exibida. |


## 🔗 Evidências 

- **C02-CT01** → [Execução](google.drive) 
- **C02-CT02** → [Execução](google.drive)  
- **C02-CT03** → [Execução](google.drive) 
- **C02-CT04** → [Execução](google.drive) 
- **C02-CT05** → [Execução](google.drive) 
