# Alterações

## v2 — reporting completo programado

- Backup do PBIP anterior preservado fora do checkout antes de editar. Original PBIX preservado.
- Mantidas ingestão contabilística, tabelas originais, IDs e relações validados; Revenue preservado.
- Custos corrigidos para débito menos crédito: motivo concreto é o estorno da conta 61 em maio de 2024, cujo Balance Period absoluto era positivo.
- Balanço implementado com saldos acumulados assinados no fim do período, sem soma de snapshots.
- Resultado líquido exige imposto aprovado; não renomeia resultado antes de imposto como líquido.
- Totais correntes e rácios exigem partes aprovadas reconciliadas, incluindo maturidades da dívida.
- Motor genérico de KPIs/comparação, planos/versionamento, estados, informações e consolidação com ajustes aprovados.
- Páginas 01–05 implementadas; 00 oculta em leitura; 06 explica KPIs. Filtros sincronizados e interações controladas.
- Integração opcional de fontes operacionais com schemas e validações; nenhum valor de projeto/cliente fabricado.
- Leitura TMDL e roundtrip com Microsoft.AnalysisServices, schemas PBIR/tema, chaves/referências, ciclos e regressões offline. Não foi executado Power BI Desktop.

## Anterior

Primeira implementação de Executive Overview e separação de fórmulas coladas em Direct Costs. Corrigida propriedade TMDL description inválida. A v2 substitui esse reporting, preservando componentes contabilísticos validados.
