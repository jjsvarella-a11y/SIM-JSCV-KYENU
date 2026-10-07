# Modelo de dados

## Preservado

Fact_Accounting, Fact_Accounting_JSCV, Fact_Accounting_KYENU, Fact_CostCenter_JSCV; RAW_ACCOUNTING_FILES e RAW por fonte; Dim_Date, Dim_Company e Dim_Account. Consultas e tabelas originais permanecem byte a byte, exceto _Measures. Relações originais mantidas. Dim_Company continua somente JSCV e KYENU. Datas automáticas existentes não foram removidas para evitar alterar dependências validadas.

## Novas dimensões e fatos

Dim_Project, Dim_Client, Dim_Unit e Dim_Contract filtram fatos por chaves únicas; cada contrato é único e um cliente pode ter vários contratos. Fact_SalesContracts, Fact_PaymentPlan e Fact_Collections compartilham dimensões; metadados de contratos são enriquecidos em Power Query. Não há relações fato-fato nem caminhos bidirecionais novos.

Fact_ProjectMetrics: grão Company ID / Project ID / Reference Date / Phase / KPI ID; valor e moeda obrigatórios. Fact_ProjectCashFlow: Company ID / Project ID / Snapshot Date / Phase / Date, distinguindo a versão conhecida na data de referência do horizonte de cash flows. As quatro fases são INITIAL, BASELINE, CURRENT, FORECAST.

Fact_IncomeTax, Fact_BalanceBreakdown, Fact_KPIPlans e Fact_Intercompany são entradas controladas do reporting, filtradas explicitamente pelas medidas. Dimensões legais não recebem uma empresa fictícia consolidada.

## Seletores e metadados

SIM_Entity, SIM_Periodicity, SIM_Comparison, SIM_ComparisonYear, SIM_ReferencePeriod, SIM_CustomStart, SIM_CustomEnd, SIM_Phase, SIM_Version, SIM_KPI, SIM_ProjectAssumptions, SIM_SourceCoverage e SIM_Refresh. As tabelas de referência de período são seletores pequenos, sem relações adicionais ao fato contabilístico.

## Tempo

O fluxo contabilístico soma o período selecionado; balanço lê somente o fim do período. Contratos são acumulados até a referência; Collections exige data efetiva e status Paid. PaymentPlan conserva Due Date e Forecast Collection Date separadamente. Datas de transações não têm uma relação de calendário ativa genérica que confunda vencimento, previsão e recebimento. As medidas aplicam a semântica temporal adequada.

Monthly: mês de referência. Quarterly: trimestre até o mês de referência. YTD: janeiro até referência. Annual: ano completo, indisponível se faltar cobertura. Gráficos corporativos de tendência usam medidas mensais, independentemente da periodicidade da matriz.

## Classificação de balanço

Contas 23–28 que exigem detalhe só entram em totais correntes após decomposição aprovada por empresa, período, conta nível 2 e classe. Ativo usa sinal positivo; passivo/equity usa sinal negativo na reconciliação com Debit YTD - Credit YTD. A soma das partes deve reconciliar a 0,01 CVE. Dívida pode ter parte corrente e não corrente, sem presumir a maturidade de toda a conta 23.

## Integridade

Chaves vazias ou duplicadas, companhias inválidas, valores monetários obrigatórios ausentes, divergências de projeto/moeda e referências de cliente/unidade/contrato/plano inválidas provocam erro de refresh nas novas fontes. Arquivos ausentes quando uma pasta operacional foi configurada também provocam erro; não são silenciosamente convertidos em tabelas vazias.
