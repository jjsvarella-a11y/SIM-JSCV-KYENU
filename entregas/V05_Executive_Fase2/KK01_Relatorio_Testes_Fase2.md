# KK-01 | V05 Executive — Relatório de Testes Fase 2

Data de referência:20/10/2026. Validação financeira em Python e recálculo externo LibreOffice. Sem Microsoft Excel Desktop disponível.

## 1. Resultado e escopo

| Verificação | Resultado |
| --- | --- |
| Controlos Python | 313 aprovados;0 falhas |
| Seletores com recálculo externo | 20 casos aprovados |
| Comparações seletores | 249834 |
| Cenários auxiliares integrados | 14 casos;164050 comparações |
| Controlos estruturais | 16 aprovados |
| Erros de célula nos recálculos finais | 0 inesperados |
| Excel Desktop | Não executado; compatibilidade não certificada |

As contagens de comparações não são números de testes independentes. Os controlos Python incluem paridade do motor original e invariantes; as comparações externas confrontam os valores recalculados com novas execuções Python. As cópias dos casos são isoladas e os inputs efetivamente modificados antes do recálculo.

## 2. Cenários executados

| Cenário | Comparações | Dividendo M54 | TIR novos 15 A |
| --- | --- | --- | --- |
| Base | 12490 | 2.630.786,91 € | 8,33% |
| Acumulados_Maximo | 12490 | 4.150.000,00 € | 8,63% |
| Acumulados_Minimo | 12490 | 3.000.000,00 € | 8,37% |
| Acumulados_Intermedio | 12490 | 3.575.000,00 € | 8,50% |
| Operador_4_3_10 | 12490 | 2.377.392,28 € | 7,65% |
| Exit_Prudente | 12490 | 2.630.786,91 € | 7,51% |
| Exit_Favoravel | 12490 | 2.630.786,91 € | 9,42% |
| Continuidade | 12490 | 2.630.786,91 € | -4,40% |
| Sem_Parcial | 12490 | 0,00 € | 7,93% |
| Suspenso | 12490 | 0,00 € | 7,60% |
| Documentado_Sem_Teto | 12490 | 0,00 € | 7,60% |
| Reserva_Extra_M54 | 12490 | 0,00 € | 8,18% |
| Hotel_Conservador | 12489 | 1.481.662,11 € | 4,23% |
| Capital_Vendas_Atraso | 12513 | 2.630.786,91 € | 8,93% |
| Documentos_M54 | 12492 | 2.630.786,91 € | 8,33% |
| Capital_75 pct | 12502 | 0,00 € | 9,36% |
| Acumulados_Max_Fallback | 12490 | 3.000.000,00 € | 8,57% |
| Exit_Reserva_Futura | 12490 | 2.630.786,91 € | 8,07% |
| Atraso_Obra_Abertura | 12488 | 0,00 € | 7,88% |
| Beneficios_NaoZero | 12490 | 2.569.453,58 € | 8,22% |

Os casos incluem os três patamares, cobertura versus acumulados, falta de capacidade/parcial/suspensão, fees 3/3/6 e4/3/10, múltiplos 10/12/15, continuidade, documentação ausente/sintética, reservas adicionais, captação parcial, atrasos e custos de benefícios não nulos. Reserva extra é proteção, não despesa fictícia. O caso de capital parcial não valida direitos societários por um preço inferior ao alvo.

## 3. Reconciliação do motor e invariantes

Compararam-se os180 meses dos campos financeiros do motor: entradas de capital e vendas, custos comerciais, CAPEX, operação, financiamento, juros/comissões, amortizações, dividendos, caixa, reservas e verificações de caixa/dívida. Verificaram-se ainda capacidades 12 M/acumulados, objetivos e fluxos dos oito blocos, incluindo as cinco parcelas G02. As TIR são obtidas dos vetores de caixa; as yields pretendidas não são usadas como TIR.

A referência preserva cada recebimento mensal de capital V04. Com a política nova desligada, a implementação Python reproduz na referência caixa, dívida, juros, dividendos e fluxo do projeto originais. Os pagamentos ordinários só ocorrem nos meses elegíveis; a cobertura 1,20 × é imposta apenas no modo Geração 12M. O parcial conserva os pesos dos objetivos mínimos. Não existem saldos automáticos de dividendos em atraso.

Verificaram-se o limite não revolving, a proteção de caixa na distribuição, a diferença entre valores estimados e recebidos na saída e a conservação dos montantes por categoria/acionista. Uma TIR não definida é texto explícito, não zero ou erro aritmético.

## 4. Riscos auxiliares preservados

| Cenário | Comparações | Falta máxima de reserva | Resultado técnico |
| --- | --- | --- | --- |
| R00 | 11713 | 0,00 € | Conforme na reconciliação |
| R01 | 11713 | 0,00 € | Conforme na reconciliação |
| R02 | 11713 | 0,00 € | Conforme na reconciliação |
| R03 | 11729 | 935.602,13 € | Conforme na reconciliação |
| R04 | 11721 | 0,00 € | Conforme na reconciliação |
| R05 | 11736 | 5.333.159,44 € | Conforme na reconciliação |
| R06 | 11719 | 1.034.416,93 € | Conforme na reconciliação |
| R07 | 11712 | 0,00 € | Conforme na reconciliação |
| R08 | 11719 | 0,00 € | Conforme na reconciliação |
| R09 | 11713 | 925.092,93 € | Conforme na reconciliação |
| R10 | 11725 | 0,00 € | Conforme na reconciliação |
| R11 | 11712 | 0,00 € | Conforme na reconciliação |
| R12 | 11712 | 0,00 € | Conforme na reconciliação |
| R13 | 11713 | 0,00 € | Conforme na reconciliação |

Conforme na reconciliação significa que as fórmulas reproduzem o cenário, não que esse cenário seja financeiramente viável. Insuficiências de reservas ou funding permanecem expostas e exigem ações; não foram anuladas com capital ou dívida fictícios.

## 5. Estrutura, tolerâncias e limitações

Os controlos preservam as folhas originais e estados,347 nomes definidos, notas, imagens, estilos e ligações. Os gráficos conservam desenho e referências; apenas caches de dados foram atualizadas a partir das mesmas células recalculadas. As fórmulas foram preservadas durante a transferência de caches, com fingerprint antes/depois. A integridade ZIP, ausência de células duplicadas, limites de comprimento e ausência de macros/links externos foram verificadas.

Tolerância externa: máximo entre 0,01€ e|valor|×1 e-9 para montantes; TIR e rácios com máximo entre 1 e-7 e|valor|×1 e-8; participação reconciliada a1 e-10. Há controlo adicional nos invariantes. Comparação de saldos do original é independente dos testes de sensibilidade. Fórmulas em cache não foram aprovadas sem recálculo externo correspondente.

Falhas de desenvolvimento e de execução paralela foram registadas e corrigidas/reexecutadas. A tabela acima apresenta apenas os resultados finais. O ambiente LibreOffice de desenvolvimento não substitui Microsoft Excel. Procedimento Microsoft ainda necessário: abrir cópia, cálculo automático, Ctrl+Alt+Shift+F9, confrontar KPI eM30/M42/M54, alterar um input e confirmar propagação. Sem essa execução não se certifica compatibilidade nativa.
