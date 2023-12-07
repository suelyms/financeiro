# financeiro

Fontes de Dados:
Dados de Execução Financeira





#DICIONÁRIO#

chave única é num_ano, cod_ne,
codigo_orgao.


id - código de identificação 

num_ano- numero do ano ( chave única)

cod_ne - codigo numero empenho(chave única)

codigo_orgao - codigo orgao ( chave única)

 dsc_orgao- descrição do orgão

 cod_credor- código credor

dsc_nome_credor- descrição do nome do credor

 cod_fonte- código da fonte

 dsc_fonte- descriçaõ de fonte

 cod_funcao- código função

dsc_funcao- descrição da função

cod_item- código item

dsc_item- descrição do item

cod_item_elemento- código ítem elemento

dsc_item_elemento- descrição do item elemento

cod_item_categoria - código  ítem categoria

dsc_item_categoria -descrição do item categoria

cod_item_grupo - código do ittem grupo

dsc_item_grupo - descrição item grupo

dsc_modalidade_licitacao - descrição modalidade licitação

cod_item_modalidade - codigo item modalidade

dsc_item_modalidade - descrição item modalidade

cod_programa - código programa

dsc_programa - descrição programa

cod_subfuncao - codigo subfunção

dsc_subfuncao -  descrição subfunção

num_sic - numero do SIC

cod_np - codigo np

vlr_empenho - valor do empenho

vlr_liquidado - valor liquidado

valor_pago - valor pago

vlr_resto_pagar - valor restante a pagar

dth_empenho - Data empenho

dth_pagamento -  Data pagamento

dth_liquidacao - Data liquidação

dth_processamento - Data processamento

num_ano_np- Numero do ano np


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



