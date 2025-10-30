## Cenário: Importação de XML de Compra

### Caso de Teste 01: Importação de XML de compra válida (Caminho Feliz)

| ID | Descrição |
| :------- | :------------------------------------------------------------------------------------------------- |
| C01-CT01 | Realizar a importação de um XML de compra válido e finalizar a entrada de produtos com sucesso. |

| **Pré-condições** |
| :----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| O usuário deve ter permissão para acessar o módulo "Importar XML de Compra".<br>O usuário deve possuir um arquivo XML de NF-e válido e acessível em seu computador.<br>Os dados do XML (produtos, fornecedor) são compatíveis com o cadastro do sistema. |

| **Passos** |
| :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **DADO** que o usuário clicou no menu "Pedido" e selecionou "Importar XML de Compra"<br>**E** preencheu o campo "CFOP Entrada" com "1102"<br>**E** selecionou "GERAL" no campo "Grupo"<br>**E** preencheu o campo "ST Entrada" com "0102"<br>**QUANDO** o usuário clicar no botão "Importar XML"<br>**E** selecionar um arquivo XML de compra válido no explorador de arquivos<br>**E** o sistema processar o arquivo e preencher a grade "Produtos no XML"<br>**E** o usuário clicar no botão "Gerar Compra"<br>**E** confirmar "Sim" na caixa de diálogo<br>**E** o sistema abrir a tela "Entrada de Produtos"<br>**E** o usuário clicar no botão "Finalizar (F2)"<br>**E** na janela "Confirmar Compra", alterar o "Status" para "CONFIRMADA"<br>**E** clicar no botão para adicionar pagamento, selecionar "PIX" como "Tipo Documento" e clicar em "Salvar (F4)"<br>**E** clicar em "Salvar (F4)" novamente na janela "Confirmar Compra"<br>**ENTÃO** a entrada de produtos deve ser concluída e salva com sucesso no sistema. |

| **Critérios de aceitação** |
| :--------------------------------------------------------------------------------------------------------------------------------------------------------- |
| A compra deve ser registrada no sistema com o status "CONFIRMADA".<br>Os produtos do XML devem ter sua entrada registrada no estoque.<br>O pagamento ("Tipo Documento") deve estar corretamente associado à compra. |

---

### Caso de Teste 02: Tentativa de importação sem preencher campos obrigatórios (Negativo)

| ID | Descrição |
| :------- | :------------------------------------------------------------------------------------------------------------------------------------ |
| C01-CT02 | O sistema não deve permitir a importação de XML quando os campos de configuração inicial (CFOP, Grupo, ST) estiverem em branco. |

| **Pré-condições** |
| :------------------------------------------------------------ |
| O usuário está na janela "Importar XML de Compra". |

| **Passos** |
| :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **DADO** que o usuário clicou no menu "Pedido" e selecionou "Importar XML de Compra"<br>**E** os campos "CFOP Entrada", "Grupo" e "ST Entrada" estão em branco<br>**QUANDO** o usuário clicar no botão "Importar XML"<br>**ENTÃO** o sistema deve exibir mensagens de validação (ex: "Campo obrigatório") abaixo de cada campo.<br>**E** a janela do explorador de arquivos não deve ser aberta. |

| **Critérios de aceitação** |
| :----------------------------------------------------------------------------------------------------------------------------------- |
| Mensagens de erro de campo obrigatório devem ser exibidas para "CFOP Entrada", "Grupo" e "ST Entrada".<br>A importação deve ser bloqueada até que os campos sejam preenchidos. |

---

### Caso de Teste 03: Tentativa de importar arquivo em formato inválido (Negativo)

| ID | Descrição |
| :------- | :----------------------------------------------------------------------------------------------------------- |
| C01-CT03 | O sistema deve falhar a importação ao tentar carregar um arquivo que não seja um XML (ex: .txt, .pdf). |

| **Pré-condições** |
| :------------------------------------------------------------------------------------------------------------------------------------------ |
| O usuário está na janela "Importar XML de Compra".<br>O usuário possui um arquivo de formato inválido (ex: "documento.txt") acessível. |

| **Passos** |
| :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **DADO** que o usuário clicou no menu "Pedido" e selecionou "Importar XML de Compra"<br>**E** preencheu os campos "CFOP Entrada", "Grupo" e "ST Entrada" corretamente<br>**QUANDO** o usuário clicar no botão "Importar XML"<br>**E** selecionar um arquivo de formato inválido (ex: "documento.txt") no explorador de arquivos<br>**ENTÃO** o sistema deve exibir uma mensagem de erro (ex: "Formato de arquivo inválido. Selecione um arquivo XML.").<br>**E** a grade "Produtos no XML" deve permanecer vazia. |

| **Critérios de aceitação** |
| :------------------------------------------------------------------------------------------------------ |
| Uma mensagem de erro clara sobre o formato do arquivo deve ser exibida ao usuário.<br>O sistema não deve tentar processar o arquivo inválido. |

---

### Caso de Teste 04: Tentativa de finalizar a compra sem adicionar forma de pagamento (Negativo)

| ID | Descrição |
| :------- | :------------------------------------------------------------------------------------------------------------------------------ |
| C01-CT04 | O sistema não deve permitir salvar a "Confirmação de Compra" sem um "Tipo Documento" (forma de pagamento) associado. |

| **Pré-condições** |
| :--------------------------------------------------------------------------------- |
| O usuário importou um XML com sucesso e está na janela "Confirmar Compra". |

| **Passos** |
| :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **DADO** que o usuário está na janela "Confirmar Compra" (após clicar em "Finalizar (F2)")<br>**E** alterou o "Status" para "CONFIRMADA"<br>**QUANDO** o usuário clicar em "Salvar (F4)" sem ter adicionado um "Tipo Documento"<br>**ENTÃO** o sistema deve exibir uma mensagem de validação (ex: "É necessário adicionar uma forma de pagamento.").<br>**E** a janela "Confirmar Compra" não deve ser fechada. |

| **Critérios de aceitação** |
| :-------------------------------------------------------------------------------------------------------------------------- |
| A validação deve impedir que a compra seja salva sem um "Tipo Documento".<br>O usuário deve ser forçado a corrigir a pendência antes de salvar. |
