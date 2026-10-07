# Páginas e filtros

| Página | Conteúdo implementado |
|---|---|
| 00 MODEL TEST | Visuais técnicos originais preservados; HiddenInViewMode. |
| 01 EXECUTIVE OVERVIEW | 4 KPIs primários, 5 secundários, tendências de resultado e balanço, comparação e matriz com leitura/estado. |
| 02 FINANCIAL PERFORMANCE | Rentabilidade, custos, P&L ordenado, mapa de contas, tendências e análise comparativa. |
| 03 BALANCE & LIQUIDITY | Caixa, clientes, fornecedores, inventário, dívida, net debt, capital e liquidez; matrizes e tendências. |
| 04 PROJECT PERFORMANCE | KPIs de investimento/execução/financiamento, metadata dinâmica e comparação das quatro fases. |
| 05 COMMERCIAL & COLLECTIONS | Vendas, cobranças reais, saldos, planos/vencimentos/previsões, clientes/unidades por contratos e inventário. |
| 06 KPI INFORMATION | Dicionário reutilizável, valores/contexto atuais, metas e fonte. |

## Interações

Company, Year, Periodicity, Period/Reference Date, Comparison, Comparison Year, Version e datas customizadas compartilham syncGroup nas páginas 01–06. Project e Phase compartilham grupos entre 04/05. Unit é filtrada ao projeto; tabelas operacionais aplicam também a empresa/data relevantes. Seleção em gráficos/tabelas não altera outros KPIs ou seletores: não são permitidos contextos mistos inadvertidos. Os seletores dirigem o contexto; a tabela de mapa de contas é informativa e o drill-down ad hoc continua disponível no Desktop via filtros de dimensão.

## Layout

Canvas 1920×1440, alinhamento consistente e tema SIM Corporate branco/preto/cinza com amarelo de acento. Vermelho é reservado a estado CRITICAL aprovado. Cards abreviam CVE/EUR em K/M; matrizes preservam os valores sem abreviação. Estado, comparação e variação acompanham os cards. A renderização e eventuais ajustes de fonte/escala precisam ser conferidos no Desktop.

## Ausência de fontes

Páginas 04/05 estão implementadas, mas não exibem os números conhecidos do handover sem fontes verificadas. Dados ausentes não são substituídos por zeros, demonstrações ou séries simuladas. O projeto permite a integração posterior pelas consultas CSV tipadas. Histórico de alterações de status de unidades/contratos não foi fornecido; UnitMaster é estado corrente, não inventário histórico. Aging por fatura exige fonte de faturas, vencimentos e liquidações própria.
