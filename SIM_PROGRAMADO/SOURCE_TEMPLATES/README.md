# Contrato das fontes opcionais

Os CSV desta pasta contêm SOMENTE cabeçalhos. Valores devem vir das fontes reais, nunca ser copiados do handover como dados confirmados.

Copiar todos os templates para uma pasta de dados antes de configurar SIM_OperationalRoot. Não preencher arquivos sem fonte: manter só o cabeçalho. Com raiz vazia, todas as fontes ficam vazias; com raiz configurada, arquivo ausente, schema errado ou chave inválida causa erro explícito. UTF-8, separador vírgula, números com ponto decimal, datas ISO YYYY-MM-DD, Approved/Complete `true` ou `false`. JSCV e KYENU são os únicos Company ID. Project Currency deve corresponder a ProjectMaster; não há conversão cambial implícita.

| CSV | Colunas |
|---|---|
| BalanceBreakdown.csv | Company ID, Period Date, Account ID, Balance Class, Value, Currency, Approved, Source |
| ClientMaster.csv | Client ID, Client Name |
| Collections.csv | Collection ID, Contract ID, Plan ID, Actual Collection Date, Amount, Currency, Status |
| Contracts.csv | Contract ID, Company ID, Project ID, Client ID, Unit ID, Contract Date, Contract Value, Currency, Status |
| IncomeTax.csv | Company ID, Period Date, Tax Expense, Approved, Source |
| Intercompany.csv | Period Date, KPI ID, Signed Adjustment, Reconciliation Status, Source |
| KPIPlans.csv | Entity Key, Project ID, Period Date, Periodicity, KPI ID, Kind, Version, Value, Limit, Excellent, Unit, Approved, Source, Desired Direction |
| PaymentPlan.csv | Plan ID, Contract ID, Due Date, Expected Amount, Forecast Collection Date, Status |
| ProjectAssumptions.csv | Project ID, Phase, Discount Rate, Source |
| ProjectCashFlow.csv | Company ID, Project ID, Date, Phase, Currency, Cash Requirement, Project Cash Available, Expected Collections, Available Financing, Available Equity, Equity Cash Flow, Snapshot Date |
| ProjectMaster.csv | Project ID, Project Name, Owner, Developer, Contractor, Status, Currency |
| ProjectMetrics.csv | Company ID, Project ID, Reference Date, Phase, KPI ID, Value, Currency, Source |
| SourceCoverage.csv | Company ID, Project ID, Feed, Reference Date, Complete, Source |
| UnitMaster.csv | Unit ID, Project ID, Currency, List Price, Area m2, Status |

## Regras específicas

- ProjectMaster: uma linha por Project ID. KY-001 deve ser fornecido pelo master real; não foi criado com valores financeiros inventados.
- ProjectMetrics: um valor por empresa/projeto/data/fase/KPI. KPI ID deve corresponder ao catálogo. Fases INITIAL/BASELINE/CURRENT/FORECAST. Percentagens em proporção (por exemplo, 0.20 representa 20%; este é exemplo de formato, não dado do projeto). Forecast Completion Value usa serial Excel; demais campos Value são numéricos na unidade do catálogo. A mesma data de snapshot deve conter os componentes necessários aos KPIs compostos.
- ProjectCashFlow: Snapshot Date identifica quando a projeção era conhecida; Date é a data de cada cash flow do horizonte. Cash Requirement e recursos são posições comparáveis de necessidade/cobertura por ponto do horizonte; não misturar saldos com fluxos incrementais sem preparar a fonte. Equity Cash Flow é entrada assinada e datada para IRR/NPV, não coleções previstas tomadas como recebidas.
- Contracts: Contract ID único, Client ID reutilizável, Unit ID existente e ligado ao Project ID. Contract Value é valor real do contrato; List Price é informação do UnitMaster, não substitui o contratado.
- PaymentPlan: Plan ID identifica cada prestação, com Due Date original e Forecast Collection Date separados. Collections deve referenciar o contrato/plano corretos, manter Actual Collection Date e valores efetivos. Status Paid e data real são obrigatórios para contar caixa efetivo. Cancelled não conta vendas ativas.
- SourceCoverage: Feed `Collections`, Complete=true e Reference Date de fim do mês certificam que a origem está completa para esse projeto/empresa. Só nesse contexto ausência de recebimentos pode ser interpretada como zero de caixa recebido.
- IncomeTax: uma linha por empresa/mês, Tax Expense aprovado e fonte documentada. Zero pode ser informado apenas quando efetivamente conhecido/aprovado.
- BalanceBreakdown: contas nível 2 23–28 que exigem detalhe podem ter várias classes; não repetir uma classe por chave. Value tem sinal normal da classe. Somar ativos positivamente e passivos/equity negativamente deve reconciliar ao Debit YTD - Credit YTD da mesma conta/período, a 0,01 CVE. Isso permite maturidades correntes/não correntes sem duplicar níveis.
- KPIPlans: Kind BUDGET/TARGET/FORECAST, Periodicity Monthly/Quarterly/YTD/Annual, entidade JSCV/KYENU/CON (CON não é entidade legal), versão explícita e Approved=true. Project ID vazio para KPI corporativo. Value deve representar exatamente esse período/periodicidade/KPI; não importar médias ou somas de ratios sem definição. Target precisa de Desired Direction Higher/Lower; Limit/Excellent opcionais precisam respeitar a ordenação. Unit deve corresponder ao KPI/moeda.
- Intercompany: uma linha por componente primitivo/mês, Signed Adjustment já com sinal da eliminação e Reconciliation Status APPROVED. Ajuste zero precisa de linha explícita. Para stocks, ajuste do snapshot; para flows, um por mês. Derivados e rácios são calculados depois dos ajustes dos componentes, não eliminados com percentagens somadas. A prova de reconciliação deve estar na fonte Source.
