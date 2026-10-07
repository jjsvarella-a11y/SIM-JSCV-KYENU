# SIM Control — especificação implementada

Continuação do projeto existente, sem reconstrução da ingestão contabilística. A referência é o PBIP em SIM_PROGRAMADO; o PBIX antigo é backup e não contém o reporting recente.

## Escopo

Páginas 01–05 implementadas em PBIR, página técnica 00 preservada e oculta no modo de leitura e página 06 com dicionário de KPIs e informação dinâmica. Medidas no _Measures, catálogo SIM_KPI, seletores desconectados e motor compartilhado de datas/comparação. Novas fontes operacionais são opcionais, tipadas e vazias até integração de fontes reais.

## Regras obrigatórias

- Revenue validado permanece idêntico, com nível 2. Nenhuma soma de todos os níveis contabilísticos.
- Custos e outros rendimentos usam o lado normal débito/crédito; estornos não se tornam custos positivos. Mudança motivada pela conta 61 de maio de 2024.
- Saldos de balanço são snapshots acumulados assinados no último dia do período.
- BLANK, zero verdadeiro, dados incompletos, fonte requerida, meta/budget/forecast ausentes, classificação e reconciliação pendentes são distintos.
- Consolidado é opção de reporting, não linha adicional em Dim_Company.
- Nenhum valor Saphire fornecido no handover foi carregado como fato sem fonte.
- Metas, limites, excelente e direção vêm somente de entradas aprovadas; não há semáforos com percentuais arbitrários.

## Limite de prontidão

O projeto e a estrutura do reporting estão implementados e verificados offline. Fontes operacionais, fiscalidade, reconciliação e maturidades continuam ausentes. A compilação DAX, o refresh M e a renderização final exigem Desktop/serviço compatível; não foram executados aqui.
