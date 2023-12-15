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



## Totais Gerais de Valor Original (Empenho)
## Totais Gerais Pago
## Totais Gerais a pagar

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

SELECT COUNT(*) AS quantidade_nulos
FROM execucao_financeira_despesa
WHERE codigo_orgao IS NULL 
or dsc_orgao is NULL
or cod_item is NULL 
or dsc_item is NULL 
or cod_item_categoria is NULL 
or dsc_item_categoria is NULL
or cod_item_grupo is NULL
or dsc_item_grupo is NULL
or dsc_modalidade_licitacao is NULL
or cod_item_modalidade is NULL
or dsc_item_modalidade is NULL

TOTAL GERAL DE NULOS: 1437212

codigo_orgao: 0
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


Duplicidade da DSC ORGAO:
SELECT dsc_orgao,COUNT(id) AS quantidade_duplicados
FROM execucao_financeira_despesa
GROUP BY dsc_orgao
HAVING COUNT(*) > 1;


SELECT dsc_orgao,COUNT(id) AS quantidade_duplicados
FROM execucao_financeira_despesa
GROUP BY dsc_orgao
HAVING COUNT(*) > 1;




**TOTAL GERAL EMPENHO**: Foi feito um SELECT SUN:

SELECT SUM(valor_empenho) AS valor_total_empenho
FROM data_warehouse.fato_empenho;
-----Valor total dos EMPENHOS:

**TOTAIS GERAIS VALOR PAGO**











   
    
    valor_pago numeric(18,2),
    
    vlr_resto_pagar numeric(18,2),
    
    dth_empenho date,
    
    dth_pagamento date,
    
    dth_liquidacao date,
    
    dth_processamento date,
    
    num_ano_np character varying COLLATE pg_catalog."default",
    
    CONSTRAINT execucao_financeira_despesa_pkey PRIMARY KEY (id)
    
);



