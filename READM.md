# GRÁFICO #

**PASSO 1**

- Guia `Dados` -> `Avançado`
-- Copiar para outro local
-- Intervalo da lista: Selecionar os dados da coluna `Unidade`
-- Marcar `Somente registros exclusivos`
-- Copiar para: escolher uma célula

Repetir os passos para `Produtos` e `Meses`


**Passo 1.2**

Selecionar os dados e nomear as celulas

**PASSO 2**

Criar os filtros `Unidade` e `Produto`na guia `Relatório`

- `Controle de Formulários` -> `Caixa de Combinação`
- Com o controle selecionado, clique com o botão direito e escolha `Formatar Controle`
- Preencher o campo `Intervalo de entrada`com o nome da lista `=lista_unidade`
- Escolher a célula para ser o `Vínculo da célula`

Repetir os passos para a lista de produtos

**Passo 2.1**

Exibir o nome da Unidade e do Produto selecionado com a fórmula `Índice`

**=INDICE(matriz;num_linha;[num_coluna])**

- matriz = lista_unidade
- num_linha = célula vinculada `no passo 2`
- num_coluna = 1


**PASSO 3**

Criar uma tabela com as colunas `Meses`, `Vendas` e `Preços`

- A coluna Meses pode ser copiada da guia `Listas`
- Na coluna `Vendas` vamos utilzar a fórmula `=SOMASES()` passando vários parâmetros que irão trazer a soma das vendas de cada produto, em cada unidade e em cada mês.

**=SOMASES(intervalo_soma;intervalo_criterios_1;criterios_1;...)**

- intervalo_soma = coluna `Vendas` da guia `Dados`
- intervalo_criterios_1 = coluna `Mês` da guia `Dados`
- criterios_1 = O mês correspondente na tabela que estamos criando
- Pressionar `F4` 3 vezes para travar a referência de letra
- criterios_2 = coluna `Unidades` da guia `Dados` 
- Após o ponto e vírgula, temos que informar o que da coluna unidades que será somado. Neste caso, a referência será o nome do municipio que exibido de acordo com o filtro. Então basta selecionar a célula correspondente.
- Em seguida pressionar `F4` para que a referência seja travada
- Por último nos resta filtrar o produto. Então vamos até a guia `Dados`, selecionamos a coluna `Produto`
- Agora selecionamos a célula de referência do produto e em seguida pressionar `F4`para travar a célula
- Terminar a fórmula fechando o parêntese e teclando `Enter`

`=SOMASES(Tabela_Vendas[Vendas];Tabela_Vendas[MÊS];RELATÓRIO!$E9;Tabela_Vendas[UNIDADE];RELATÓRIO!D2;Tabela_Vendas[PRODUTO];RELATÓRIO!$D$4)`

- Por último, arrastar a fórmula para as linhas seguintes

**Passo 3.1**

Repetir os passos acima, alerando o primeiro critério de `Tabela_Vendas[Vendas];` para `Tabela_Vendas[Preço];`

No caso do preço, também poderia ser utilizada a fórmula `=MEDIASES()`


**PASSO 4 Criando o Gráfico**

- Selecionar a tabela auxiliar
- Inserir -> Gráfico de Colunas -> Mais Gráficos de Colunas -> Combinação -> Coluna Clusterizada - Eixo Secundário

*Perfumaria - Título do Gráfico Dinâmico*

Em uma célua qualquer, faremos:

="Unidade: "&D2&" - Produto: "&D4

Em seguida, selecionar o título do gráfico, e na barra de fórmulas indicar a célula acima.