# Fontes que ainda faltam

Os arquivos BG/BCC recebidos foram reconciliados ao PBIX: 96 arquivos mensais, mais 6 arquivos dos períodos 13/15 preservados e excluídos do filtro mensal existente. BCC agosto de 2026 foi recuperado. O BCC contém descrições como Departamento de Obras - Saphir, Empreendimento Saphir e Saphire, mas o Record Type está vazio no snapshot recebido. Falta um mapeamento aprovado de centro/conta/nível para Project ID e natureza do movimento. Estas referências não autorizam somar níveis da hierarquia nem validar os valores de KY-001. Não foram encontrados os registos adicionais necessários de contratos, prestações, recebimentos, snapshots de investimento e metas.

| Fonte necessária | Operação que desbloqueia |
|---|---|
| Imposto mensal aprovado / reconciliação fiscal | Net Result e Net Margin; não presumir imposto zero. |
| Partes de balanço classificadas por mês, conta e maturidade | Current Assets / Current Liabilities / Working Capital e rácios; partes devem reconciliar ao BG. |
| Reconciliação intercompany e ajustes assinados aprovados | Valores consolidados; exigir zero explícito quando não há ajuste. |
| Project Master, snapshots de investimento/GDV, fases e execução | KY-001 Saphire, GDV/EAC/ROI/CPI/SPI/progresso e forecast completion. |
| Cash flow de projeto versionado, taxa de desconto e dívida | Funding Gap/Peak/IRR/NPV/DSCR sem suposições inventadas. |
| Client Master, Unit Master e contratos reais | Vendas, clientes, unidades disponíveis/reservadas, preços e áreas. |
| Payment Plan e recebimentos datados/alocados | Collections/receivables/overdue/expected, sem tratar previsões como dinheiro recebido. |
| Cobertura completa aprovada da fonte de recebimentos | Permitir zero verdadeiro de cobranças e calcular saldos por prestação sem assumir feed incompleto como ausência de pagamentos. |
| Planos/KPI targets/versionamento aprovados | Budget/Target/Forecast, limites e estados de desempenho. |
| Faturas/fornecedores e liquidações com vencimento | Aging de fornecedores/clientes e DSO/DPO não aproximados. |

Integração pelas consultas tipadas de SOURCE_TEMPLATES; readaptar para os arquivos originais Excel quando forem fornecidos, sem exigir recriação manual de informação já existente. A lista de fontes ausentes é uma limitação real, não uma lista de dados preenchidos automaticamente.
