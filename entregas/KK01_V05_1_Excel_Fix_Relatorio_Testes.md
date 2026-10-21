# KK-01 V05.1 Excel Fix — relatório de testes

21/10/2026. Estado: Conforme nos testes executados; aceitação Microsoft Excel Desktop pendente.

| Caso nativo | Estado | Comparações | Falhas | Erros |
|---|---|---|---|---|
| Base | Conforme | 1127557 | 0 | 0 |
| IVA_Diferido | Conforme | 19426 | 0 | 0 |
| Div_Maximo_Acumulados | Conforme | 19416 | 0 | 0 |
| Juro8 | Conforme | 19417 | 0 | 0 |
| PT_EN | Conforme | 19416 | 0 | 0 |
| Filtro_ID201 | Conforme | 19416 | 0 | 0 |

Comparações nativas/Python totais: 1.224.648. O caso Base abrange os 62 motores; os outros casos verificam o fluxo de 180 meses, retornos e os seletores alterados. Os snapshots verificam erros de fórmula em todas as folhas. Os testes são executados por cliente Java/UNO externo, sem macros no workbook, numa cópia privada cujo SHA-256 é 2b534f0602277e532f1e9672604c7cde26a3e0b544e76785ecf5ffc097a5999a.

| Verificação | Resultado |
|---|---|
| Pacote ZIP / relações / índices | Conforme; 104 partes de relações verificadas, 364 nomes definidos preservados. |
| Esquemas OOXML — antes | V05: 9 ocorrências; V05.1: 44 ocorrências, no perfil documentado. |
| Esquemas OOXML — depois | 470 partes; zero violações. |
| Fórmulas existentes | 2.126.479 comparadas; nenhuma alteração. |
| Valores numéricos existentes | 2.134.128 comparados; nenhuma alteração. |
| Dicionário KPI | 40 KPI; delta zero. |
| Regressão financeira Python | 10 grupos aprovados. |
| Regressão estrutural | 3 mutações inválidas rejeitadas e fundo do cartão TIR verificado. |
| Visualização | Nove painéis renderizados em PDF; cartão TIR branco, texto vermelho no cenário atual. |
| Excel Desktop | Não executado; abertura sem recuperação e aparência nativa pendentes. |

Não foram alterados os critérios financeiros de alerta para melhorar a aparência. As fórmulas de formatação condicional mantêm-se; a apresentação da TIR passa a usar apenas cores de fonte. A prova de preservação, o comparativo CSV e os registos por componente acompanham esta entrega.
