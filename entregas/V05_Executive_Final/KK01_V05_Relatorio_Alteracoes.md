# KK-01 V05 — Relatório de alterações

21/10/2026. Preservação do V04 Excel Fix e da entrega anterior. Alterações atuais sobre a camada financeira anterior: 664987células registadas em 185 folhas, incluindo fórmulas auxiliares e textos; não são664987erros da V04.

## Módulos

Capital:8calendários próprios, separação caixa KK/secondary e propagação às48sensibilidades e13riscos. Financiamento: motor não renovável preservado; novas despesas e reservas fiscais ligadas à disponibilidade, draw, juros, serviço e sweep. IVA: pago/dedutível/reembolsado/compensado/pendente/não recuperável, com bases líquidas ou IVA incluído. IRPC: EBT, prejuízos, lucro tributável, incentivos elegíveis, acréscimo/pagamento e dívida fiscal. Atos/IPI: titularidade, pagador e calendário. Seguros: adicionais versus incluídos, taxas dinâmicas, CAPEX/OPEX.

Dividendos: lucros de estudo e retenção prudencial, proteção de impostos, cobertura12M ou acumulados, parcial e documentação separada. Exit: IRPC por pagar deduzido; projeto distingue impostos sem escudo financeiro. Interface: nove painéis, gráficos e filtros comerciais, dicionárioPT/EN, fontes e navegação. Histórico, capítulos/EAC/ETC, trimestres, fontes fiscais e análises anuais ficam em folhas técnicas.

## Evidências

Registo_Alteracoes_Formulas.json.gz contém folha/célula/fórmula anterior/nova e motivo. Alteracoes_por_Folha.csv sintetiza o volume. Registo_Fase2_Anterior.json.gz cobre o percurso da V04 à camada anterior. A atualização de caches apenas transfere valores recalculados e não substitui fórmulas. Reconciliacao_Caches_Final.json prova a identidade das fórmulas antes/depois dessa transferência.

As folhas e dashboards legados foram preservados com avisos de contexto; não devem ser lidos como uma segunda política financeira. Todos os novos painéis consultam o mesmo motor. As decisões externas continuam identificadas em V05 Parametros, fontes fiscais e registo de pressupostos.
