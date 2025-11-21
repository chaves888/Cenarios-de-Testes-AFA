### Caso de Teste 1: Cadastro de cliente com sucesso
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C4-CT1	 | Cadastro básico deve ser salvo corretamente.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Usuário que está fazendo o cadastro tem que ter permissão de cadastrar usuários.|

| **Passos**                                             |
| :------------------------------------------------------------ |
|DADO que usuário clica em “Novo”|
|E preenche os campos obrigatórios|
|QUANDO clicar em Salvar|
|ENTÃO cliente deve aparecer na lista de consulta.|

| **Critérios de Aceitação**                                             |
| :------------------------------------------------------------ |
|Cadastro salvo.|
| Teste evidenciado e aprovado|
| https://drive.google.com/file/d/18fAptmhE6LAc79kIf0PH36KWqfhm3thd/view?usp=drive_link |

### Caso de Teste 02: Exclusão de Cliente cadastrado sem uso na tabela de venda
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C4-CT2	 | Sistema deleta o usuário e mantém mostrando a listagem.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Cliente cadastrado no sistema.|

| **Passos**                                             |
| :------------------------------------------------------------ |
|DADO que o usuário acessa a tela de cadastro de cliente|
|E selecionamos o cliente sem uso na tabela VENDA para ser excluído|
|QUANDO clica em excluir|
|ENTÃO o sistema exclui o cliente selecionado.|

| **Critérios de Aceitação**                                             |
| :-------------
|----------------------------------------------- |
|Alerta exibido.|
|Teste evidenciado e aprovado|
| https://drive.google.com/file/d/1GNVpr3PuOs6Ke6Ycr6VzjklR-A-UfZvx/view?usp=drive_link |

### Caso de Teste 3: Tentar salvar cliente sem preencher campos obrigatórios
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C4-CT3	 | Sistema deve impedir cadastro incompleto.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Nenhuma.|

| **Passos**                                                        |
| :------------------------------------------------------------ |
|DADO que o usuário deixa o CEP vazio|
|QUANDO tentar salvar|
|ENTÃO deve exibir alerta de erro que o Endereço não foi preenchido.|

| **Critérios de Aceitação**                                             |
| :------------------------------------------------------------ |
|Cadastro bloqueado.|
|Teste evidenciado e aprovado|
| https://drive.google.com/file/d/1548g8MpUUf5_KEuokrFQ_FM9OyXEXTfA/view?usp=drive_link |