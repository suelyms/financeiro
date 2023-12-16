## TRABALHO DESAFIO FINAL

## 1º PASSO: RESTAURAR OS DADOS ENVIADO PELO PROF. -Importação do dump/backup para um banco de dados Relacional (SQL);


# financeiro -  Fontes de Dados:
Dados de Execução Financeira

## VERIFICANDO E ANALISANDO A TABELA

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




### CRIANDO ODS.

CREATE TABLE ods.execucao_financeira_despesa as
SELECT *FROM execucao_financeira_despesa;



## ANÁLISE EXPLORATÓRIA DA TABELA

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


**VERIFICAR DUPLICIDADE EM CADA CAMPO:

Em relação ao Identificador Serial de Registro, não existe duplicidade.

## AO CRIAR A CHAVE UNICA, JÁ EXCLUÍMOS AS DUPLICATAS, PARA EVITAR FUTURAS DUPLICAÇÕES:

![image](https://github.com/suelyms/financeiro/assets/142910077/6ba2f190-8977-47cc-ba62-f7f1b05dd6ca)






**TOTAL GERAL EMPENHO**: Foi feito um SELECT SUN:

![image](https://github.com/suelyms/financeiro/assets/142910077/8fd0d2d1-2b1b-46fb-a25e-90889415558e)

-----Valor total dos Empenho:



**TOTAIS GERAIS VALOR PAGO**

![image](https://github.com/suelyms/financeiro/assets/142910077/3e3fc7ff-b694-4d98-bad8-a3308487773c)



**TOTAIS GERAIS A PAGAR**

![image](https://github.com/suelyms/financeiro/assets/142910077/364c65ae-c433-4f99-9114-db30498dacbb)



### Análise por Orgão:** Total Empenho, Total Pago e Total A Pagar

**Total por ano

![image](https://github.com/suelyms/financeiro/assets/142910077/f39db6aa-0884-42de-ac77-534f401b8ef1)



   **Total por bimestre

   ![image](https://github.com/suelyms/financeiro/assets/142910077/e391d3f9-fc88-47d0-8419-656062168ebb)



    **Total por mês
    
 ![image](https://github.com/suelyms/financeiro/assets/142910077/53205367-e559-41dd-8f4e-161641795130)



 ## Análise por item_elemento:**  Total Empenho, Total Pago e Total A Pagar


**Total por ano
![image](https://github.com/suelyms/financeiro/assets/142910077/9f167e3b-b6ce-4554-b829-b7c77b59b9b6)


** Total por bimestre

![image](https://github.com/suelyms/financeiro/assets/142910077/8d71ad18-99a4-4587-bf87-3f5e5a35ee5b)


** Total por mes
![image](https://github.com/suelyms/financeiro/assets/142910077/1f328d63-e670-4b66-9a11-47ddca060bf0)


 ## Análise por Item Categoria:** Total Empenho, Total Pago e Total A Pagar

   
    **Total por ano
![image](https://github.com/suelyms/financeiro/assets/142910077/400d08ed-a41f-441f-89bb-149b75131ec5)



    **Total por bimestre
    
![image](https://github.com/suelyms/financeiro/assets/142910077/76d8b4d4-5222-49f5-9e26-2d208129d444)


    **Total por mes
![image](https://github.com/suelyms/financeiro/assets/142910077/303ff2cc-f304-49ff-a0f0-5c7eaf132b70)

    
    
   

