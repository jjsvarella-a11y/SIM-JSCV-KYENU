# Motor DAX

Revenue foi preservado. Descrições TMDL usam comentários `///` reconhecidos pelo parser oficial, sem propriedades `description:` inválidas.

## Arquitetura

KPI Base seleciona o cálculo; KPI Entity Value aplica a empresa; KPI Actual aplica o intervalo; KPI Comparative reutiliza o mesmo cálculo no intervalo comparativo ou lê plano aprovado. KPI Variance e KPI Variance % exigem bases presentes; denominador zero resulta indefinição explícita.

Comparações: Homologous Period, Previous Period, Same Period of Selected Year, Custom, Budget, Target e Forecast. Previous Period em YTD fica explicitamente indisponível, pois não há definição de negócio aprovada; não foi inventada uma comparação. Comparação customizada requer início/fim válidos. Dados de planos precisam corresponder exatamente a entidade/projeto, período, periodicidade, KPI, versão, unidade e aprovação; não se somam ratios mensais para criar metas anuais.

KPI Status diferencia NO DATA, SOURCE REQUIRED, NO TARGET, NO BUDGET/FORECAST na comparação, INCOMPLETE PERIOD, PENDING MAPPING, PENDING RECONCILIATION, TAX SOURCE REQUIRED, cobertura de recebimentos ausente e zero denominador. EXCELLENT / ON TARGET / ATTENTION / CRITICAL só usam metas e direção aprovadas. Bandas incoerentes são sinalizadas, não utilizadas.

## Consolidação

KPI Consolidated Atom exige ambos os valores legais conhecidos e ajustes assinados APPROVED para cada período. Fonte de zero eliminação precisa conter zero explícito aprovado. KPI Consolidated Value deriva margens, EBITDA, resultado, capital circulante e rácios após os ajustes dos componentes. Não se somam percentagens ou resultados legais sem eliminações. Ainda não há fonte de eliminações neste projeto.

## Convenções financeiras

Net Result = Result Before Tax - Income Tax aprovado; sem imposto não há resultado líquido. DSO/DPO são proxies com saldo final, receita/custos diretos do intervalo e dias do intervalo: não são aging nem substituem compras/IVA ajustados. ROI foi explicitamente definido como Profit on Cost, conforme o handover; não é rentabilidade sobre equity. NPV exige taxa anual fornecida; XIRR exige fluxos datados com ambos os sinais. Funding Gap/Peak usam requisitos e recursos da mesma versão de cash flow, sem recursos ausentes tratados como zero.

## KPIs programados

| KPI ID | Unidade | Fonte | Fórmula / regra |
|---|---|---|---|
| Revenue | CVE | Accounting BG | SUM Balance Period, group Revenue |
| Direct Costs | CVE | Accounting BG | SUM Debit Period - SUM Credit Period, account 61 |
| Gross Profit | CVE | Accounting BG | Revenue - Direct Costs |
| Gross Margin | % | Accounting BG | Gross Profit / Revenue |
| FSE | CVE | Accounting BG | Debit Period - Credit Period, account 62 |
| Payroll | CVE | Accounting BG | Debit Period - Credit Period, account 63 |
| Other Operating Costs | CVE | Accounting BG | Debit Period - Credit Period, account 68 |
| Other Operating Income | CVE | Accounting BG | Credit Period - Debit Period, account 78 |
| EBITDA | CVE | Accounting BG | Revenue + Other Operating Income - Direct Costs - FSE - Payroll - Other Operating Costs |
| EBITDA Margin | % | Accounting BG | EBITDA / Revenue |
| D&A | CVE | Accounting BG | Debit Period - Credit Period, account 64 |
| EBIT | CVE | Accounting BG | EBITDA - D&A |
| EBIT Margin | % | Accounting BG | EBIT / Revenue |
| Finance Costs | CVE | Accounting BG | Debit Period - Credit Period, account 69 |
| Finance Income | CVE | Accounting BG | Credit Period - Debit Period, account 79 |
| Net Finance | CVE | Accounting BG | Finance Income - Finance Costs |
| Result Before Tax | CVE | Accounting BG | EBIT + Net Finance |
| Net Result | CVE | Accounting BG | Result Before Tax - Income Tax |
| Net Margin | % | Accounting BG | Net Result / Revenue |
| Cash | CVE | Accounting BG | Debit YTD - Credit YTD, accounts 11/12/13 |
| Accounts Receivable | CVE | Accounting BG | Debit YTD - Credit YTD, account 21 |
| Accounts Payable | CVE | Accounting BG | Credit YTD - Debit YTD, account 22 |
| Inventory / WIP | CVE | Accounting BG | Debit YTD - Credit YTD, accounts 35/36 |
| Current Assets | CVE | Accounting BG | Mapped Current Assets + approved current-asset classifications |
| Current Liabilities | CVE | Accounting BG | Payables + approved current-liability classifications |
| Working Capital | CVE | Accounting BG | Current Assets - Current Liabilities |
| Debt | CVE | Accounting BG | Credit YTD - Debit YTD, account 23 |
| Net Debt | CVE | Accounting BG | Debt - Cash |
| Equity | CVE | Accounting BG | Credit YTD - Debit YTD, accounts 51/56/58/59 |
| Current Ratio | x | Accounting BG | Current Assets / Current Liabilities |
| Quick Ratio | x | Accounting BG | (Current Assets - Inventory) / Current Liabilities |
| Immediate Liquidity | x | Accounting BG | Cash / Current Liabilities |
| DSO | days | Accounting BG | Receivables / Revenue * selected days |
| DPO | days | Accounting BG | Payables / Direct Costs * selected days |
| GDV | currency | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | sum project GDV |
| Initial Investment | currency | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | source Initial Investment |
| Current Investment | currency | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | source Current Investment |
| Investment Variance | currency | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | Current Investment - Initial Investment |
| Project Profit | currency | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | GDV - Current Investment |
| Development Margin | % | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | Project Profit / GDV |
| Profit on Cost | % | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | Project Profit / Current Investment |
| ROI | % | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | Project Profit / Current Investment |
| IRR | % | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | XIRR dated equity cash flows |
| NPV | currency | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | dated cash flows discounted at sourced rate |
| Financing | currency | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | source Financing |
| Project Equity | currency | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | source Project Equity |
| LTC | % | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | Financing / Current Investment |
| LTV | % | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | Financing / GDV |
| Funding Coverage | % | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | available cash + expected receipts + finance + equity / requirements |
| Funding Gap | currency | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | max(0, requirements - available resources), latest period |
| Peak Funding Gap | currency | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | MAX Funding Gap over sourced projection dates |
| Physical Progress | % | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | source Physical Progress |
| Financial Progress | % | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | Actual Cost / Current Investment |
| Actual Cost | currency | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | source Actual Cost |
| Committed Cost | currency | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | source Committed Cost |
| Cost to Complete | currency | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | Current Investment - Actual Cost |
| CPI | x | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | Earned Value / Actual Cost |
| SPI | x | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | Earned Value / Planned Value |
| Forecast Completion | date | ProjectMetrics / ProjectCashFlow / ProjectAssumptions | source Forecast Completion date |
| Contracted Sales | currency | Contracts / PaymentPlan / Collections / UnitMaster | approved/non-cancelled contracts through reference date |
| Collections | currency | Contracts / PaymentPlan / Collections / UnitMaster | actual dated receipts only |
| Commercial Receivables | currency | Contracts / PaymentPlan / Collections / UnitMaster | Contracted Sales - Collections |
| Remaining GDV | currency | Contracts / PaymentPlan / Collections / UnitMaster | GDV - Contracted Sales |
| Overdue Receivables | currency | Contracts / PaymentPlan / Collections / UnitMaster | past-due payment plans minus actual plan receipts |
| Collection Rate | % | Contracts / PaymentPlan / Collections / UnitMaster | Collections / Contracted Sales |
| % Sold | % | Contracts / PaymentPlan / Collections / UnitMaster | Contracted Sales / GDV |
| Units Sold | units | Contracts / PaymentPlan / Collections / UnitMaster | distinct units in active contracts |
| Units Reserved | units | Contracts / PaymentPlan / Collections / UnitMaster | unit master status Reserved |
| Units Available | units | Contracts / PaymentPlan / Collections / UnitMaster | unit master status Available |
| Average Selling Price | currency | Contracts / PaymentPlan / Collections / UnitMaster | Contracted Sales / Units Sold |
| Average Price m2 | currency | Contracts / PaymentPlan / Collections / UnitMaster | Contracted Sales / area of distinct sold units |
| Sales Velocity | contracts/month | Contracts / PaymentPlan / Collections / UnitMaster | distinct contracts in selected period / selected months |
| Expected Collections | currency | Contracts / PaymentPlan / Collections / UnitMaster | future forecast-dated plan residuals; not actual cash |
| DSCR | x | Contracts / PaymentPlan / Collections / UnitMaster | cash available for debt service / debt service; source required |
| Earned Value | currency | ProjectMetrics | source Earned Value |
| Planned Value | currency | ProjectMetrics | source Planned Value |
| Cash Available for Debt Service | currency | ProjectMetrics | source Cash Available for Debt Service |
| Debt Service | currency | ProjectMetrics | source Debt Service |
| Income Tax | CVE | IncomeTax | approved tax source monthly |

## Medidas adicionais

REPORTING_MEASURES.json contém o código completo das medidas novas/revisadas. O TMDL é a definição usada pelo Power BI. A validação offline não executa essas expressões no motor DAX.
