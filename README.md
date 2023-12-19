## TRABALHO DESAFIO FINAL

## 1º PASSO: RESTAURAR OS DADOS ENVIADO PELO PROF. -Importação do dump/backup para um banco de dados Relacional (SQL);


# financeiro -  Fontes de Dados:
Dados de Execução Financeira

## VERIFICANDO

SELECT  num_ano, cod_ne, codigo_orgao, count(*) from execucao_financeira_despesa 
group by  num_ano, cod_ne, codigo_orgao having count(*)>1


##  2º PASSO: FOMULAR O DICIONÁRIO 
# #DICIONÁRIO

| NOME VARIÁVEL | DESCRIÇÃO E TIPO DE VARIÁVEL|POSSUI VALORES NULOS|
|---|---|---|
| id | Identificador Serial do Registro - (PK)INTERGER|NÃO|
|---|---|
| num_ano   |Numero do ano do empenho  - chave única -NOT NULL|NÃO|
|---|---|
|cod_ne |Codigo de identificação do numero do empenho - chave única-NOT NULL|NÃO|
|---|---|
|codigo_orgao | Codigo que identifica o orgao responsável - Character varying(NOT NULL)|NÃO|
|---|---|
|dsc_orgao | Nome do orgão responsável pela despesa- Character varying |NÃO|
|---|---|
|cod_credor| código que identifica o credor -Character varying|NÃO|
|---|--|
| dsc_nome_credor | Nome do credor que tem direito ao recebimento -Character varying|NÃO|
|---|---|
| cod_fonte| código da fonte dos recursos-Character varying|SIM|
|---|---|
|dsc_fonte| descriçaõ de fonte dos recursos utilizados para realizar os pagamentos-Character varying|SIM|
|---|---|
| cod_funcao |código que identifica a função a qual está relacionada a despesa-Character varying|NÃO|
|---|---|
|dsc_funcao| Função a qual a despesaestá relacionada -Character varying|NÃO
|---|---|
|cod_item| código do item especifico relacionado a despesa -Character varying|SIM|
|---|---|
|dsc_item |descrição do item relacionado a despesa -Character varying|SIM|
|---|---|
|cod_item_elemento| código ítem que identifica o elemento de despesa -Character varying|SIM|
|---|---|
|dsc_item_elemento| descrição do item elemento que indentifica a natureza do gasto -Character varying|SIM|
|---|---|
|cod_item_categoria | código  ítem categoria -Character varying|NÃO|
|---|---|
|dsc_item_categoria |descrição do item categoria-Character varying|NÃO|
|---|---|
|cod_item_grupo | código do ittem grupo-Character varying|SIM|
|---|---|
|dsc_item_grupo | descrição item grupo -Character varying|SIM|
|---|---|
|dsc_modalidade_licitacao | descrição modalidade licitação -Character varying|
|---|---|
|cod_item_modalidade |codigo item modalidade -Character varying|NÃO|
|---|---|
|dsc_item_modalidade | descrição item modalidade -Character varying|NÃO|
|---|---|
|cod_programa | código que identifica um programa específico relacionado a despesa- Character varying|NÃO|
|---|---|
|dsc_programa | descrição programa relacionado a despesa-Character varying|NÃO|
|---|---|
|cod_subfuncao | codigo subfunção -|Character varying|NÃO|
|---|---|
|dsc_subfuncao | descrição da subfunção em qual a despesa está relacionada -Character varying|NÃO|
|---|---|
|num_sic | numero do SIC -Numero de identificação do Sistema integrado de adm. financeira, utilizado para controle e registro das informações|SIM|
|---|---|
|cod_np | codigodo numero do processo -Character varying|NÃO|
|---|---|
|vlr_empenho | valor reservado para pagamento da despesa -NUMERIC(18,2)|NÃO|
|---|---|
|vlr_liquidado | valor utilizado para pagamento da despesa -NUMERIC(18,2)|NÃO|
|---|---|
|valor_pago | valor desembolsado para pagar a despesa-NUMERIC(18,2)SIM|
|---|---|
|vlr_resto_pagar | valor que ainda precisa ser pago para pagar a despesa -NUMERIC(18,2)|NÃO|
|---|---|
|dth_empenho | Data e hora do empenho, indicando quando foi realizado  -DATE|
|---|---|
|dth_pagamento |  Data e hora do pagamento indicando quandoocorreu o desembolso -DATE|SIM|
|---|---|
|dth_liquidacao | Data e hora da liquidação, indicando quando ocorreu  -DATE|SIM|
|---|---|
|dth_processamento | Data e hora do processamento, indicando quando foi atualizados -DATE|NÃO|
|---|---|
|num_ano_np | Numero do ano associado aonúmero do Processo - Character varying|SIM|







## 3º PASSO: Fazer a Modelagem Conceitual do banco de dados importado acima;


![image](https://github.com/suelyms/financeiro/assets/142910077/8f97be8b-25e9-47b9-8f1b-ae03061a6e20)


## 4º passo: MODELAGEM LÓGICA:

![image](https://github.com/suelyms/financeiro/assets/142910077/4b685845-5d65-4e14-b681-b9e55aaf254d)



## 5ºPASSO: MODELAGEM DIMENSIONAL:

![image](https://github.com/suelyms/financeiro/assets/142910077/5f6ff40c-ca43-4c0a-afb3-41fdf0e271c6)


## 6º PASSO: CRIANDO A TABELA SQL


- Totais Gerais de Valor Original (Empenho)
- Totais Gerais Pago
- Totais Gerais a pagar

---MEDIDAS ACIMA POR:

- Período (ano, bimestre e mês);
 
- Órgão;
  
- Item: Item Elemento, Item Categoria, Item Grupo;
  
- Período (ano, semestre e mês);
  
- Modalidade: item modalidade, modalidade licitação;




- CRIANDO ODS.

CREATE TABLE ods.execucao_financeira_despesa as
SELECT *FROM execucao_financeira_despesa;




## 7º PASSO: ANÁLISE EXPLORATÓRIA DA TABELA

- Durante a análise detalhada da tabela de despesas, identifiquei uma série de irregularidades nos dados,
incluindo a presença de campos vazios, valores nulos e a existência de valores negativos que não condizem 
com o total esperado. Essas observações levantam preocupações significativas sobre a integridade dos dados registrados.



FOI EXTRAÍDOS DADOS DE UMA EXECUCAO FINANCEIRA,  REFERENTES A PAGAMENTOS DE EMPENHOS

SENDO A CHAVE ÚNICA:  num_ano, cod_ne, codigo_orgao.

* Independente de os dados terem sido coletados eles precisam ser interpretados para atingir os objetivos propostos
da pesquisa. O passo inicial para isso é realizar a Análise Exploratória de Dados para resumir e
organizar os dados, de maneira que seja possível identificar padrões e elaborar as primeiras conclusões a respeito
e assim descrever a sua variabilidade.


## OBJETIVOS: Aferição de medidas: 


- Período (ano, bimestre e mês);
  Órgão;
  Item: Item Elemento, Item Categoria, Item Grupo;

- Período (ano, semestre e mês);
  Órgão;
  Modalidade: item modalidade, modalidade licitação

  OBS> DE INICIO SÓ SERÁ POSSIVEL A ANALISE POR ANO.


  - PRIMEIRAMENTE EXECUTEI UM COMANDO PARA EXIBIR AS 5 PRIMEIRAS LINHAS PARA TER UMA VISÃO INICIAL:

  ![image](https://github.com/suelyms/financeiro/assets/142910077/8ecbf451-d0ee-44e9-bfee-ecddf7b1dfbb)

  Durante a análise inicial da tabela de despesas, observei a presença de campos vazios em diversas colunas,
   indicando a falta de informações cruciais para o entendimento e a interpretação adequada dos registros.
  Os campos afetados incluem os campos: dsc_item_grupo, cod_item_grupo, num_sic, vlr_liquidado, vlr_resto_pagar e dth_liquidacao




- VERIFIQUEI CAMPOS NUMÉRICOS, como média, mínimo, máximo de empenho:

![image](https://github.com/suelyms/financeiro/assets/142910077/d25ae5c6-cedb-4f6b-99d4-54160454beb8)



![image](https://github.com/suelyms/financeiro/assets/142910077/283791b9-cbe3-4352-824e-c9796b06f075)


 - Observei uma situação peculiar que requer atenção especial: o valor mínimo dos empenhos está negativo.
   Essa descoberta levanta considerações importantes sobre a integridade e a consistência dos dados registrados.






NESSA TABELA INICIAL VERIFIQUEI  O VALOR TOTAL DE EMPENHO 

![image](https://github.com/suelyms/financeiro/assets/142910077/63924cbb-e04c-48ff-a63e-9db60f38a961)

DANDO UM VALOR TOTAL DE EMPENHO: 1337468033892.24

* Valor Total do Empenho Excessivamente Elevado

Durante a análise minuciosa da tabela de despesas, chama a atenção a presença de um valor total de empenho que se destaca por sua extrema elevação. Essa observação levanta considerações importantes sobre a integridade dos dados e pode indicar possíveis problemas ou eventos extraordinários. Abaixo estão algumas observações preliminares sobre essa constatação:

Valor Total Anormalmente Alto:

O valor total do empenho na tabela de despesas é significativamente superior às expectativas normais, indicando a presença de um montante excessivamente elevado.

1. Possíveis Causas:
A origem desse valor pode ser atribuída a diferentes fatores, como erros na entrada de dados, registros duplicados, falhas nos processos de integração, ou mesmo a ocorrência de eventos incomuns que resultaram em despesas extraordinárias.

3. Impacto na Análise Financeira:
A existência desse valor excessivo pode distorcer a análise financeira, comprometendo a interpretação precisa dos gastos e influenciando decisões estratégicas baseadas nessas informações.

4.Validação e Verificação:
É imperativo realizar uma validação minuciosa dos registros associados a esse valor total elevado. Isso pode envolver a verificação da fonte dos dados, revisão de processos de entrada e a confirmação da precisão das transações relacionadas.

5.Correções Necessárias:
Se identificado como um erro, será necessário corrigir os registros afetados, ajustando os valores para refletir a realidade das despesas. Se for resultado de eventos extraordinários, é crucial documentar e explicar esses eventos para garantir a transparência na análise.



VERIFICANDO  POR ORGÃO VIMOS QUE TIVEMOS PAGAMENTO PARA ORGÃOS EM QUE A DESCRIÇÃO ESTÁ NULA
![image](https://github.com/suelyms/financeiro/assets/142910077/edf65bdc-d47f-4e18-b01a-4cec41a26c74)
![image](https://github.com/suelyms/financeiro/assets/142910077/23eaa78a-b705-4bdb-9af0-5a4eade59ea3)
![image](https://github.com/suelyms/financeiro/assets/142910077/3e68d85f-c74b-44f7-b55e-13b10a5ee8d1)


- Ao realizar uma análise exploratória na tabela de despesas, observei uma particularidade que merece atenção:
a presença de campos vazios na descrição do órgão (campo dsc_orgao). 
A descrição do órgão é uma informação crucial para entender o contexto e a natureza das despesas registradas, 
e a ausência desses dados pode impactar a qualidade da análise e interpretação dos resultados.






ANALISANDO A TABELA, VERIFICAMOS NULOS, DUPLICIDADE, VALORES..

VERIFICANDO TOTAL GERAL DE NULOS:

![image](https://github.com/suelyms/financeiro/assets/142910077/80ab05d3-a46f-45cc-b693-09ed2ca38f83)


TOTAL GERAL DE NULOS: 1437212

id:codigo_orgao: 0

dsc_orgao:116

cod_item: 287982

dsc_item: 287982

cod_item_categoria: 0

dsc_item_categoria: 0

cod_item_grupo: 1134605

dsc_item_grupo: 1134605

dsc_modalidade_licitacao:401656

cod_item_modalidade: 0

dsc_item_modalidade:0


## AO CRIAR A CHAVE UNICA, JÁ EXCLUÍMOS AS DUPLICATAS, PARA EVITAR FUTURAS DUPLICAÇÕES:

![image](https://github.com/suelyms/financeiro/assets/142910077/6ba2f190-8977-47cc-ba62-f7f1b05dd6ca)




**TOTAIS GERAIS VALOR PAGO**

![image](https://github.com/suelyms/financeiro/assets/142910077/f8840995-d7ef-4020-9643-8ce5d07f2e07)

![image](https://github.com/suelyms/financeiro/assets/142910077/7bd09623-21ea-48e6-838a-28386a8eed38)




**TOTAIS GERAIS A PAGAR**

![image](https://github.com/suelyms/financeiro/assets/142910077/e45adc15-2fd4-4d8f-905a-43aca347e521)

![image](https://github.com/suelyms/financeiro/assets/142910077/5c46f86a-89bb-449c-8002-8ea82bf29341)





### Análise por Orgão:** Total Empenho, Total Pago e Total A Pagar

**Total por ano

![image](https://github.com/suelyms/financeiro/assets/142910077/94aca699-5c50-496f-a710-082e19a68068)

![image](https://github.com/suelyms/financeiro/assets/142910077/9f21f0d3-3e0d-4b1c-91f6-c733c33c85f5)

Em alguns registros, o campo "Valor Total a Pagar" está vazio, mesmo quando os valores de empenho e pagamento estão preenchidos.
A ausência do valor total a pagar pode ser resultado de erros na entrada de dados, problemas de integração entre sistemas, ou mesmo a falta de atualização dos registros.


 

 ## Análise por item_elemento:**  Total Empenho, Total Pago e Total A Pagar

**Total por ano
![image](https://github.com/suelyms/financeiro/assets/142910077/079fe34b-73c7-4c7a-929e-d6fea0037dcd)
Em alguns registros, o campo "Valor Total a Pagar" está vazio, mesmo quando os valores de empenho e pagamento estão preenchidos.
A ausência do valor total a pagar pode ser resultado de erros na entrada de dados, problemas de integração entre sistemas, ou mesmo a falta de atualização dos registros.



 ## Análise por Item Categoria:** Total Empenho, Total Pago e Total A Pagar
   
    **Total por ano
    
    ![image](https://github.com/suelyms/financeiro/assets/142910077/4f04ef44-ca8d-42cc-afed-a8160f33bb7d)
    
Em alguns registros, o campo "Valor Total a Pagar" está vazio, mesmo quando os valores de empenho e pagamento estão preenchidos.
A ausência do valor total a pagar pode ser resultado de erros na entrada de dados, problemas de integração entre sistemas, ou mesmo a falta de atualização dos registros.




  
    
    
   

