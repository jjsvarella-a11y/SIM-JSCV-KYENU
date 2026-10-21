# KK-01 V05 — Documentação técnica

21/10/2026. Workbook OOXML sem VBA,180 meses e resumos anuais15 anos. Construído por alterações controladas sobre a V04 Fixed, preservando os componentes originais e a camada financeira anterior.

## Fluxo de dados

Pressupostos/Cenarios/Unidades/Obra + V05 Captacao/V05 Parametros → recebimentos/CAPEX/operação/capital + auxiliares fiscais em cada motor → Fluxo180M e61alternativas → reservas/dividendos → V04Waterfall180/V04Retornos/V05Blocos → V05Anual/V05KPI/V05Dados → nove ecrãs. CONFIG_LANGUAGE/DIC_TRANSLATIONS alimentam apenas apresentação.

## Novas folhas

V05 Parametros: inputs fiscais/seguros e limites. V05 IVA Comp: capacidade KK por mês. V05 Captacao:8 blocos e origens. V05 Escrituras:94 frações e3atos potenciais. V05 Historico:4,5M separados da caixa futura. V05 Capitulos: contratado/realizado/ETC/EAC de controlo. V05 Trimestres: agregação mensal. V05 Anual:15 anos. V05 Fontes Fiscais: entidade/incidência/estado. V05 Seguros: bases e prémios. V05 Proprietarios: rateio informativo. V05 Sensibilidades:48 motores dinâmicos. V05 KPI: definições e fontes. V05 Dados/V05 RE A/B: fontes de gráficos, ocultas. CONFIG_LANGUAGE/DIC_TRANSLATIONS/V05 Listas: idioma e validações. Nove ecrãs: EXEC V05, DASH01V05, DASH02, DASH03V05, DASH04AV05, DASH04BV05, DASH05V05, DASH06V05, DASH07V05; os nomes efetivos incluem os espaços visíveis no Excel.

## Fórmulas críticas

IVA suportado=(construção+fiscalização líquidas)×taxa. Crédito pendente=saldo inicial+IVA dedutível−compensação−reembolso. Não recuperável integra custo, sem nova duplicação de caixa. Compensação limita-se à capacidade da mesma entidade e aos créditos temporalmente elegíveis.

Lucro da promoção=preço transmitido−quota de custo de construção/seguro/IVA não recuperável−custos comerciais/ITI KK. Quota de área é hipótese. Resultado operacional tributável=EBITDA Hotel+MICE+residualKK−depreciação−juros/encargos. EBT consolidado desconta atos/IPI/outros encargos modelados; compensa prejuízos de estudo. IRPC é anual, com efeito de incentivos limitado ao lucro elegível. Pagamento é separado da competência; o passivo fiscal final reduz o Equity Value.

A retenção prudencial de 5% e a proxy de resultados não certificam lucros legalmente distribuíveis. Valores documentados usam caps e aprovação próprios. O serviço obrigatório inclui principal/juros/encargos mandatórios e exclui sweep. O CFADS consolidado inclui efeitos dos impostos pagos, explicitando que não é imposto autónomo exclusivo do Hotel.

O projeto usa impostos sem o escudo de financiamento na TIR/VPL de projeto, evitando mudar esse retorno apenas por alterar juros. Fluxos de equity incluem financiamento, dividendos e saída. A base histórica não é repetida no CF futuro; métricas de projeto futuro são incrementais. Payback é determinado após o último saldo acumulado negativo; o retorno acionista depende dos fluxos próprios.

EV=Múltiplo×EBITDA M169–180. Equity=EV−custos−dívida−crédito acionista+caixa−HOTUSA/contingência−reserva adicional−IRPC por pagar, limitado a zero. Reserva operacional protege a exploração e não é abatida automaticamente como perda na venda; confirmar normalização de fundo de maneio/caixa com comprador. Não reavaliar apartamentos vendidos. Saída40/10/50; ordinários por objetivos de categoria, sem preferências adicionais.

## Datas e limitações

Meses do projeto não são datas de contratos. Data inicial01/11/2026 e vetor uniforme365/12 são convenções editáveis para XIRR; sem dados individuais não há TIR histórica comprovada. As bases tributáveis/proprietários/incentivos/seguro são hipóteses não certificadas. Não há importação automática de extratos, contabilidade, apólices ou registos societários.

## Código e regressões

model.py reutiliza o corpo do motor mensal V04 e injeta cálculos fiscais sequenciais. financial.py gera fórmulas OOXML equivalentes. build.py preserva partes e junta folhas/estilos/desenhos/validações. interface.py constrói os nove ecrãs. test_model.py testa invariantes e paridade desligada. validate.py compara valores; NativeScenarios.java altera seletores via UNO e desativa macros. audit_live.py reconcilia cenários e reabre a referência com 62 motores. merge_caches.py atualiza apenas valores e caches dos gráficos, provando identidade das fórmulas. audit_structure.py verifica o pacote, relações, fórmulas, folhas, nomes, gráficos e validações.

O pacote de fontes inclui referências Python e metadados necessários. Para gerar o workbook são necessárias as duas bases Excel indicadas no README_Fontes, disponíveis nas entregas anteriores; não estão duplicadas no pacote. Testar futuras alterações com os mesmos casos e acrescentar casos para novos ramos lógicos. Os testes financeiros nativos não certificam Excel Desktop.
