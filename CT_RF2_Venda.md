### Caso de Teste 1: Produto sem estoque
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C2-CT1	 | Sistema deve impedir venda sem estoque.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Produto com quantidade menor que a quantidade escolhida pra realizar a venda (no nosso caso está negativo o número do item).|

| **Passos**                                                        |
| :------------------------------------------------------------ |
|DADO que o usuário tenta incluir o produto|
|QUANDO selecionar quantidade|
|ENTÃO deve exibir mensagem “Estoque insuficiente”.|

| **Critérios de Aceitação**                                             |
| :------------------------------------------------------------ |
|Produto não deve entrar na venda.|
|Teste realizado e reprovado: Produto sem estoque e venda foi finalizada normalmente|
|https://drive.google.com/file/d/1BDq-WQRLhimwLddrFCOdjoGDINm9ZtEk/view?usp=drive_link|


### Caso de Teste 2: Finalizar venda não selecionando o tipo de documento
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C2-CT2	 | Sistema deve impedir finalização sem forma de pagamento.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Venda pronta para finalizar.|

| **Passos**                                                        |
| :------------------------------------------------------------ |
|DADO que o usuário está na tela final|
|QUANDO clicar em “Salvar” sem escolher tipo de documento|
|ENTÃO deve exibir erro.|

| **Critérios de Aceitação**                                             |
| :------------------------------------------------------------ |
|Finalização bloqueada.|
|Teste evidenciado e aprovado|
|https://drive.google.com/file/d/1tbWMQLWqH6IMVMP_fu-MQbVsJBXPXMsw/view?usp=drive_link|


### Caso de Teste 3: Completar venda com mais de 1 tipo de item
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C2-CT3	 | Venda registrada, estoque reduzido e caixa alimentado.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Cliente, funcionário e produtos cadastrados.|

| **Passos**                                                        |
| :------------------------------------------------------------ |
|DADO que o usuário clica em **Novo** na tela de vendas|
|E escolhe cliente, funcionário e data|
|E insere produtos|
|E adiciona novo produto diferente do anterior (shorts por exemplo)|
|QUANDO finalizar e salvar|
|ENTÃO a venda deve aparecer uma mensagem de compra finalizada.|

| **Critérios de Aceitação**                                         |
| :------------------------------------------------------------ |
|Estoque atualizado.|
|Caixa alimentado.|
|Teste realizado e evidenciado|
|https://drive.google.com/file/d/1zjx85EqkwtVNZ0bLUpjM8UcIOhBlB_GX/view?usp=drive_link|