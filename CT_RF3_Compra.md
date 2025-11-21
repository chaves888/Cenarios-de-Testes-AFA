### Caso de Teste 1: Compra finalizada com sucesso
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C3-CT1	 | Compra lançada, estoque atualizado e caixa alimentado.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Fornecedor cadastrado.|
|Produto cadastrado.|

| **Passos**                                                        |
| :------------------------------------------------------------ |
|DADO que o usuário cria nova compra|
|E adiciona produtos|
|QUANDO finalizar compra|
|ENTÃO estoque deve ser alimentado com os itens comprados.|

| **Critérios de Aceitação**                                             |
| :------------------------------------------------------------ |
|Compra CONFIRMADA.|
| Teste evidenciado e aprovado|
| https://drive.google.com/file/d/1er3e1nt6ku-KAXpa9B9LkDDdQ_J0_W1V/view?usp=drive_link|


### Caso de Teste 2: Fornecedor não infomado.
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C3-CT2	 | Deve impedir compra sem fornecedor.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Nenhuma.|

| **Passos**                                                        |
| :------------------------------------------------------------ |
|DADO que usuário tenta criar compra sem inserir código ou nome de fornecedor|
|QUANDO clicar em **Salvar**|
|ENTÃO sistema deve mostrar uma mensagem de erro.|

| **Critérios de Aceitação**                                             |
| :------------------------------------------------------------ |
| Mensagem “Código Fornecedor não foi preenchido”.|
| Teste evidenciado e aprovado|
| https://drive.google.com/file/d/11vk6k5aOAQVVZkkXl86Q-OZZPVMIoXgF/view?usp=drive_link |

### Caso de Teste 3: Fornecedor cadastrando corretamente
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C3-CT3	 | Fornecedor cadastado no sistema, e redirecionado para a tela de fornecedores.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Nenhuma.|

| **Passos**                                                        |
| :------------------------------------------------------------ |
|DADO que usuário acessa a tela criar fornecedores|
|E preencher os dados necessários para cadastros|
|QUANDO clicar em **Salvar**|
|ENTÃO o sistema deve cadastrar um novo fornecedor.|

| **Critérios de Aceitação**                                             |
| :------------------------------------------------------------ |
| Teste evidenciado e reprovado, deu erro no campo de CEP, mesmo colocando um CEP válido|
| https://drive.google.com/file/d/1KsFjJyIR8skaf9nYULzOZoew8l026cEk/view?usp=drive_link |