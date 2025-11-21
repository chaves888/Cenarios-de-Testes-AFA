### Caso de Teste 1: Realizar retirada de valores com sucesso.

| ID       | Descrição                                                            |
| :------- | :------------------------------------------------------------------- |
| C5-CT1 | Permitir o registro de uma retirada de valores. |

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
| Caixa deve estar aberto e possuir saldo suficiente.  |

| **Passos**                                                        |
| :---------------------------------------------------------------- |
| DADO que o operador acessa o Caixa             |
| E clica em “Retirar Valores”                                           |
| E informa o valor e o motivo |
| QUANDO confirmar a operação                                    |
| ENTÃO a retirada deve ser listada e descontada do saldo do caixa |

| **Critérios de aceitação**                                      |
| :-------------------------------------------------------------- |
| A retirada deve aparecer no extrato do caixa e reduzir o saldo disponível. |
| Teste evidenciado e aprovado|
| https://drive.google.com/file/d/1r_e3dtzaK-cfL13TNOzZeeIMW5P1SpnG/view?usp=drive_link |


### Caso de Teste 02: Tentativa de retirada maior que o saldo disponível.

| ID       | Descrição                                                                       |
| :------- | :------------------------------------------------------------------------------- |
| C5-CT2 | O sistema deve impedir uma retirada quando o valor exceder o saldo em caixa. |

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
| Caixa deve estar aberto.       |
| Caixa deve ter um valor menor que o que estamos retirando de saldo.       |

| **Passos**                                                        |
| :---------------------------------------------------------------- |
| DADO que o usuário tenta realizar uma retirada             |
| E informa um valor maior que o saldo atual                                           |
| QUANDO clicar em confirmar                                    |
| ENTÃO o sistema deve exibir mensagem de erro |

| **Critérios de aceitação**                                      |
| :-------------------------------------------------------------- |
| A retirada não deve ser registrada.                             |
| Mensagem deve indicar “Valor não pode ser maior que o existente em saldo de caixa”. |
| Teste evidenciado e aprovado|
| https://drive.google.com/file/d/13hDM_uJDSAWvyZ6i_9QXAzDKveVOEe_E/view?usp=drive_link |


### Caso de Teste 03: Gerando relatório de fechamento de caixa".

| ID       | Descrição                                                      |
| :------- | :------------------------------------------------------------- |
| C5-CT3 | O sistema deve mostrar toda a movimentação no relatório gerado no fechamento de caixa. |

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
| O caixa deve estar fechado. |

| **Passos**                                                        |
| :---------------------------------------------------------------- |
| DADO que o usuário acessa o Livro Caixa (fechado) |
| E que o usuário clica em Imprimir Caixa           |
| E seleciona a opção Normal                |
| QUANDO gerar o relatório                                  |
| ENTÃO os totais de vendas devem bater com os totais do caixa |

| **Critérios de aceitação**                                      |
| :-------------------------------------------------------------- |
| Diferença deve ser igual a zero.       |
| Se houver divergência, o sistema deve sinalizar.|
| Teste evidenciado e aprovado|
| https://drive.google.com/file/d/1I13BSHQliyRVTvvnsXRr6OvdB-tIbiAj/view?usp=drive_link |