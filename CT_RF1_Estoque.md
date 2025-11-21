### Caso de Teste 1: Importação XML inválido
| ID       | Descrição                                                        |
| ------- | ---------------------------------------------------------------- |
|C1-CT1	 | Sistema deve recusar XML inválido.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
| - XML com estrutura incorreta.|
| - Usuário ter permissão pra Importar XML.|

| **Passos**                                                        |
| :------------------------------------------------------------ |
|DADO que o usuário acessa Pedidos > Importar XML de Compra|
|E seleciona um XML corrompido|
|QUANDO clicar em “Importar XML”|
|ENTÃO deve aparecer erro e bloqueio da ação.|

| **Critérios de aceitação**                                      |
| :------------------------------------------------------------ |
|Mensagem de erro ou aviso que o XML não importou nada.|

|Teste realizado e evidenciado|
|https://drive.google.com/file/d/1cTm5D3Wp5sViF_szMLfCwxYsQo8FhPvc/view?usp=drive_link|

### Caso de Teste 2: Importação do XML de forma correta e gerar compra
| ID       | Descrição                                                       |
| ------- | ---------------------------------------------------------------- |
|C1-CT2	 | Importação de XML válido alimenta estoque corretamente.         |

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
| - XML válido.                                       |
| - Usuário ter permissão pra Importar XML.           |
| - Produtos existentes na nota.                      |
| - Ter valor suficiente para a realização da compra em Caixa (usamos o método dinheiro)|

| **Passos**                                                                 |
| :------------------------------------------------------------ |
|DADO que o usuário acessa Pedidos > Importar XML de Compra|
|E preenche CFOP, Grupo e ST Entrada|
|E importa um XML válido|
|E clicar em “Gerar Compra” e depois “Finalizar”|
|E Selecionou o STATUS de "Não confirmada" para “Confirmada”|
|E Selecionou o Tipo de Documento "DINHEIRO" e clicou em “Salvar”|
|ENTÃO o estoque deve ser atualizado e a compra aparecer como “CONFIRMADA”.|

| **Critérios de aceitação**                                      |
| :------------------------------------------------------------ |
|Compra confirmada.|
|Produtos lançados no estoque.|

|Teste realizado e evidenciado|
|https://drive.google.com/file/d/1_qJEi4Mb_xRyWA4dQ0gnEZze_phGPwZu/view?usp=drive_link|

### Caso de Teste 3: Falta de preenchimento obrigatório
| ID       | Descrição                                                        |
| ------- | ---------------------------------------------------------------- |
|C1-CT3	 | Bloqueio da importação sem CFOP ou Grupo ou ST Entrada.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
| - Usuário ter permissão pra acessar a página de Importar XML.|

| **Passos**                                                        |
| :------------------------------------------------------------ |
|DADO que o usuário está na tela|
|E deixa CFOP ou Grupo em branco|
|QUANDO tentar importar XML|
|ENTÃO deve exibir mensagens de “campo obrigatório”.|

| **Critérios de aceitação**                                      |
| :------------------------------------------------------------ |
|Campos obrigatórios validados.|
|Testes realizados e evidenciados|
|https://drive.google.com/file/d/16rU4wQCHS-6j8BvuYg-wsEcB0yAuMmQg/view?usp=drive_link|


### Caso de Teste 4: Gerar compra mas não confirmar entrada
| ID       | Descrição                                                        |
| ------- | ---------------------------------------------------------------- |
|C1-CT4	| Compra deve permanecer "NÃO CONFIRMADA" sem confirmação.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
| - XML válido importado.|
| - Ter acesso à area de consulta de compras.|

| **Passos**                                                        |
| :------------------------------------------------------------ |
|DADO que o usuário gera a compra|
|QUANDO sair da tela sem mudar o status para CONFIRMADA|
|ENTÃO a compra deve ficar com status "NÃO CONFIRMADA" e não afetar o estoque, nem mostrar na filtragem quando consultadas as compras confirmadas.|

| **Critérios de aceitação**                                    |
| :------------------------------------------------------------ |
|Estoque não alterado.|
|Teste realizado e evidenciado|
|https://drive.google.com/file/d/1gHpeZgKNDMotrka5YFi_DGgNNDNMuSBH/view?usp=drive_link|