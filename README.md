## TRABALHO DESAFIO FINAL

## 1º PASSO: RESTAURAR OS DADOS ENVIADO PELO PROF. -Importação do dump/backup para um banco de dados Relacional (SQL);


# financeiro -  Fontes de Dados:
Dados de Execução Financeira

## VERIFICANDO E ANALISANDO A TABELA

SELECT  num_ano, cod_ne, codigo_orgao, count(*) from execucao_financeira_despesa 
group by  num_ano, cod_ne, codigo_orgao having count(*)>1


##  2º PASSO: FOMULAR O DICIONÁRIO 
#DICIONÁRIO#

chave única é num_ano, cod_ne,
codigo_orgao.


    
 id - código de identificação (PRIMARY KEY)

 num_ano   -numero do ano ( chave única)

cod_ne - codigo numero empenho(chave única)

codigo_orgao - codigo orgao ( chave única)

 dsc_orgao- descrição do orgão (VARCHAR)

 cod_credor- código credor (INT)

dsc_nome_credor- descrição do nome do credor (VARCHAR)

 cod_fonte- código da fonte (INT)

 dsc_fonte- descriçaõ de fonte (VARCHAR)

 cod_funcao- código função(INT)

dsc_funcao- descrição da função (VARCHAR)

cod_item- código item (INT)

dsc_item- descrição do item (VARCHAR)

cod_item_elemento- código ítem elemento (INT)

dsc_item_elemento- descrição do item elemento (VARCHAR)

cod_item_categoria - código  ítem categoria (INT)

dsc_item_categoria -descrição do item categoria(VARCHAR)

cod_item_grupo - código do ittem grupo(INT)

dsc_item_grupo - descrição item grupo (VARCHAR)

dsc_modalidade_licitacao - descrição modalidade licitação (VARCHAR)

cod_item_modalidade - codigo item modalidade (INT)

dsc_item_modalidade - descrição item modalidade (VARCHAR)

cod_programa - código programa (INT)

dsc_programa - descrição programa(VARCHAR)

cod_subfuncao - codigo subfunção (INT)

dsc_subfuncao -  descrição subfunção (VARCHAR)

num_sic - numero do SIC (INT)

cod_np - codigo np(INT)

vlr_empenho - valor do empenho (NUMERIC)

vlr_liquidado - valor liquidado (NUMERIC)

valor_pago - valor pago(NUMERIC)

vlr_resto_pagar - valor restante a pagar (NUMERIC)

dth_empenho - Data empenho (DATE)

dth_pagamento -  Data pagamento (DATE)

dth_liquidacao - Data liquidação (DATE)

dth_processamento - Data processamento (DATE)

num_ano_np- Numero do ano np ( default)


## 3º PASSO: Fazer a Modelagem Lógica do banco de dados importado acima;



TABELA FINANCEIRA


CREATE TABLE  public.execucao_financeira_despesa
(
    id integer NOT NULL DEFAULT nextval('execucao_financeira_despesa_id_seq'::regclass),
    
    num_ano character varying COLLATE pg_catalog."default" NOT NULL,
    
    cod_ne character varying COLLATE pg_catalog."default" NOT NULL,
    
    codigo_orgao character varying COLLATE pg_catalog."default" NOT NULL,
    
    dsc_orgao character varying COLLATE pg_catalog."default",
    
    cod_credor character varying COLLATE pg_catalog."default",
    
    dsc_nome_credor character varying COLLATE pg_catalog."default",
    
    cod_fonte character varying COLLATE pg_catalog."default",
    
    dsc_fonte character varying COLLATE pg_catalog."default",
    
    cod_funcao character varying COLLATE pg_catalog."default",
    
    dsc_funcao character varying COLLATE pg_catalog."default",
    
    cod_item character varying COLLATE pg_catalog."default",
    
    dsc_item character varying COLLATE pg_catalog."default",
    
    cod_item_elemento character varying COLLATE pg_catalog."default",
    
    dsc_item_elemento character varying COLLATE pg_catalog."default",
    
    cod_item_categoria character varying COLLATE pg_catalog."default",
    
    dsc_item_categoria character varying COLLATE pg_catalog."default",
    
    cod_item_grupo character varying COLLATE pg_catalog."default",
    
    dsc_item_grupo character varying COLLATE pg_catalog."default",
    
    dsc_modalidade_licitacao character varying COLLATE pg_catalog."default",
    
    cod_item_modalidade character varying COLLATE pg_catalog."default",
    
    dsc_item_modalidade character varying COLLATE pg_catalog."default",
    
    cod_programa character varying COLLATE pg_catalog."default",
    
    dsc_programa character varying COLLATE pg_catalog."default",
    
    cod_subfuncao character varying COLLATE pg_catalog."default",
    
    dsc_subfuncao character varying COLLATE pg_catalog."default",
    
    num_sic character varying COLLATE pg_catalog."default",
    
    cod_np character varying COLLATE pg_catalog."default" DEFAULT 0,
    
    vlr_empenho numeric(18,2),
    
    vlr_liquidado numeric(18,2),
    
    valor_pago numeric(18,2),
    
    vlr_resto_pagar numeric(18,2),
    
    dth_empenho date,
    
    dth_pagamento date,
    
    dth_liquidacao date,
    
    dth_processamento date,
    
    num_ano_np character varying COLLATE pg_catalog."default",
    
    CONSTRAINT execucao_financeira_despesa_pkey PRIMARY KEY (id)
    
);



