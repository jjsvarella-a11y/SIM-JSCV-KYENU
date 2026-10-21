# KK-01 V05 Executive — Diagnóstico da Fase 1

20/10/2026 | Fonte: KK01_Modelo_Integrado_V04_Excel_Fix.xlsx

## 1. Conclusão e âmbito

A V04 Fixed constitui uma base reutilizável. A auditoria desta fase não modificou fórmulas, pressupostos, direitos ou dashboards. Foi preservada uma cópia integral do original. Não foi ainda produzida a V05 funcional: o mandato exige aprovação após este diagnóstico e antes das alterações estruturais da Fase 2.

A implementação V05 altera a economia das distribuições e da saída; não é apenas uma reformatação. Recomenda-se preservar o motor mensal e atualizar, de modo coordenado, composição dos blocos, pipeline, capital realizado, dividendos, waterfall, retornos e cenários auxiliares. Não se devem transportar pesos de remuneração antigos para a nova estrutura.

## 2. Evidência técnica atual

- 313 folhas: 64 visíveis e 249 ocultas.
- 1.485.103 fórmulas; 347 nomes definidos, incluindo nomes locais e técnicos.
- 17 gráficos; 36 referências a desenhos, que também podem incluir imagens.
- 886 regras de validação e 553 elementos de hiperligação.
- Nenhuma tabela estruturada OOXML identificada; os detalhes existentes usam intervalos/filtros. A conversão em tabelas deve ser seletiva.
- Nenhum código de erro armazenado em células; nenhuma ligação externa de workbook ou macro VBA encontrada.
- Cálculo automático, recálculo integral ao abrir e iteração desativada.
- Não foram encontradas fórmulas marcadas como matriciais no OOXML. Isto não prova ausência de operações sobre intervalos.
- Integridade ZIP verificada e SHA-256 da cópia igual ao original: be8288ced2494ef31c2dbe1d31d77b8277a0753a1209a8df0a83c3a5d86dcdc0.

O inventário completo está no CSV Mapa_Folhas_V04.csv. Dependencias_Entre_Folhas.csv identifica referências explícitas entre folhas; não é um grafo completo de todas as células nem uma prova de ausência de circularidades. Nomes e fórmulas relevantes ficam registados no JSON do inventário e na cópia original.

## 3. Mapa do motor e tratamento proposto

| Módulo | Folhas principais | Tratamento V05 |
|---|---|---|
| Pressupostos | Pressupostos, Cenarios, Listas | Preservar fonte central; acrescentar política V05 e metadados documentais |
| Construção | Obra, CAPEX, V04 CAPEX Base, V04 EAC | Preservar orçamento, calendário e separação histórico/futuro |
| Promoção | Unidades, Recebimentos, Imobiliario, V04 Pricing, V04 Comercial, V04 Metas RE | Preservar 94 IDs, preços e recebimentos; melhorar filtros e distinguir realizado/projetado |
| Hotel + MICE | Hotel, Operador, Condicoes Operador, V04 Operacional | Preservar operação dos 200 quartos; integrar comparação de fees |
| Residencial | Residencial, DASH Residencial | Preservar pool e residual KK; acrescentar análise por unidade sem prometer yields |
| Capital | Capital V03, Blocos V03, Matriz Societaria V03, V04 Pipeline, V04 Capital180 | Atualizar para 15 blocos; novo pipeline de 8 blocos de investidores |
| Financiamento | Fluxo 180M, V04 Bancabilidade, V04 Completion | Preservar motor único e limite não revolving; propagar nova política |
| Dividendos e retorno | V04 Politica, V04 Waterfall180, V04 Retornos, Fluxos Retorno, Retorno Categorias V03 | Atualização estrutural; calendário operacional e elegibilidade mensal |
| Síntese e cenários | Anual, Comparacao, Resultados Cenarios, V04 Riscos, V04 Impactos, folhas Calc e V04 R01–R13 | Preservar e atualizar dependências; evitar comparativos com política antiga sem identificação |
| Auditoria | AUDITORIA, KPI, V04 Dicionario KPI, Origem e Alteracoes | Preservar, atualizar fórmulas e estados de validação |
| Interface | EXEC KK01, dashboards existentes | Preservar até substituição validada; sete ecrãs novos nas Fases 3/4 |

Fluxo principal: pressupostos + unidades + capítulos de obra + pipeline → recebimentos/CAPEX/operação/capital → Fluxo 180M → Anual/KPI/distribuições/retornos → dashboards, riscos e dicionário. A política de dividendos é limitada pela caixa e compromissos do mês; a valorização terminal não deve financiar dividendos anteriores à venda.

## 4. Fotografia financeira reconciliada da V04

| Indicador | V04 Fixed |
|---|---:|
| Frações | 94: 36 T1, 36 T2, 18 T3 e 4 Penthouse |
| Área privativa residencial | 13.290 m² |
| VGV | 50.656.336,37 € |
| CAPEX futuro de referência | 63.168.000,00 € |
| Capital KK previsto no cenário | 25.000.000,00 € |
| Pico intramensal da dívida | 14.883.293,59 € |
| Utilização bancária acumulada | 19.187.648,01 € |
| Caixa mínima em 180 meses | 3.633.802,73 € |
| Caixa / dívida / reserva M30 | 8.717.152,56 € / 0 € / 3.633.802,73 € |
| Caixa / dívida / reserva M42 | 7.760.803,63 € / 0 € / 3.000.000,00 € |
| Caixa / dívida / reserva M54 na V04 | 7.758.489,22 € / 0 € / 3.000.000,00 € |
| Dividendos pagos no próprio M54 na V04 | 0 € |
| EBITDA segundo ano operacional M43–M54 | 5.012.848,61 € |
| EBITDA Ano 15 do projeto M169–M180 | 7.760.809,12 € |
| TIR / MOIC novos investidores 15 anos | 7,85% / 2,48× |
| VPL novos investidores a 12% | −8.358.003,30 € |
| Payback do projeto sem saída — referência V04 | 86 meses |

Os saldos M54 refletem a política existente na V04 e o seu histórico de distribuições, não o resultado da futura política V05. Caixa acima da reserva não equivale, por si, a dividendo legalmente distribuível. O payback do projeto não é o payback dos acionistas.

## 5. Alterações estruturais expressamente pedidas

### 5.1 Blocos e captação

V04: JSCV 1 Platinum + 2 Gold; JALS 5 Silver; novos 1 Platinum + 1 Gold + 10 Silver. Total 2 Platinum, 3 Gold, 15 Silver: 20 blocos.

V05: JSCV 2 Platinum; JALS 5 Silver; novos 1 Platinum + 2 Gold + 5 Silver. Total 3 Platinum, 2 Gold, 10 Silver: 15 blocos. Mantêm-se 40% / 10% / 50%, e a captação-alvo mantém-se em 25 M€. Os novos investidores passam de 12 para 8 blocos. Os blocos convencionais dos promotores não geram novo dinheiro.

Requer atualização de contagens, identificadores, calendário de captação, entradas efetivas e cenários. O segundo Gold não deve herdar silenciosamente as datas dos Silver substituídos. Proposta para estudo: preservar o calendário agregado de capital da V04 quando possível, documentando qualquer diferença por bloco; não declarar esse calendário como compromisso contratual.

### 5.2 Dividendos

Primeiro pagamento elegível M54; depois M66, M78, M90, M102, M114, M126, M138, M150, M162 e M174: 11 datas. Sem dividendos ordinários M1–M53 e sem dividendo ordinário extra implícito no M180.

Totais anuais conferidos por composição: mínimo 3.000.000 €; intermédio 3.575.000 €; máximo 4.150.000 €. Estes são objetivos globais sobre bases convencionais, não dívidas nem garantias.

Proposta de implementação a validar na Fase 2: patamar automático mais elevado que cumpra cobertura de 1,20× com caixa gerada nos 12 meses anteriores, além do limite independente de caixa acumulada livre, serviço obrigatório, reservas e compromissos. Lucros distribuíveis documentados e aprovação societária constituem um controlo separado. Se existir apenas proxy, o resultado é simulado/condicional, não juridicamente elegível nem efetivamente pago.

Distribuição parcial: propor rateio sobre o objetivo mínimo de cada categoria, mantendo igualdade por bloco da mesma categoria; não introduzir senioridade Platinum sem aprovação. Patamares não satisfeitos são informação, sem acumulação automática de crédito. As regras do período de cobertura e rateio parcial devem ser confirmadas com a aprovação da arquitetura.

### 5.3 Saída

Substituir a referência V04 de 9× por cenários 10× / 12× / 15×, com 12× como referência Base proposta no mandato. Com o EBITDA V04 do Ano 15, EV ilustrativo de 77.608.091,20 €, 93.129.709,44 € e 116.412.136,80 €, antes dos ajustamentos. Não são Equity Values nem novas previsões V05.

M180 é o fecho do Ano 15 e a fronteira de entrada no Ano 16; a venda no fim de M180 usa o EBITDA M169–M180. A continuidade mantém valor terminal recebido igual a zero, distinguindo valor económico estimado de caixa realizável.

Equity Value deve deduzir custos, dívida e obrigações aplicáveis e incorporar caixa livre uma única vez. Não reavaliar apartamentos vendidos. A menor distribuição ordinária pode aumentar caixa terminal; este efeito deve ser reconciliado.

O mandato não fixa a nova chave de repartição da saída entre categorias. A V04 usava pesos otimizados para as antigas metas de TIR e contagens. Não os transportar automaticamente. Recomenda-se usar repartição proporcional à participação económica como cenário de estudo, com preferências alternativas separadas e assinaladas como propostas. A regra precisa de validação antes de ser apresentada como política V05.

## 6. Interface, bilingue e limitações nativas do Excel

Criar os sete ecrãs pedidos, mantendo folhas técnicas e dashboards antigos até confirmar substituição. CONFIG_LANGUAGE e DIC_TRANSLATIONS servirão textos e séries dos gráficos por referências; títulos, legendas, interpretações e dicionário devem acompanhar PT/EN sem alterar números.

Sem macros, várias células editáveis em dashboards distintos não se sincronizam bidirecionalmente por fórmulas. Usar uma única célula de input por parâmetro e mostrar espelhos com ligação ao controlo central nos outros ecrãs. Isto também se aplica ao idioma. Listas de filtros de visualização podem ser locais quando não forem pressupostos financeiros.

O restauro sem VBA deve funcionar por seleção de cenário Referência/Personalizado; fórmulas não reescrevem células manuais. Reservar inputs personalizados e conservar valores de referência separados.

A moeda deve manter EUR, ou apresentar conversão meramente visual com taxa documentada. Não criar uma nova hipótese cambial sem identificação. RevPAR é calculado a partir de ADR e ocupação; eventual override requer modo próprio para evitar pressupostos contraditórios.

Ícones de informação devem ligar ao dicionário bilingue com navegação de regresso. Comentários estáticos existentes serão preservados; novos textos dinâmicos não devem depender da tradução automática desses comentários.

Nomes de folhas Excel têm limite de 31 caracteres: usar nomes curtos EXEC, DASH 01, DASH 02A, DASH 02B, DASH 03, DASH 04, DASH 05, com os títulos completos nas células. Não renomear arbitrariamente folhas usadas pelo motor.

A comparação de dois operadores deve reutilizar fórmulas ou cenários auxiliares parametrizados, sem criar uma segunda lógica financeira independente. As regressões devem verificar propagação até dividendos, caixa, EV e retorno.

## 7. Achados e pendências

- Alerta documental confirmado: a nota de Pressupostos relativa a KK-E25 ainda diz «25 M€ por 49%», embora a estrutura calculada seja 50%. Corrigir texto e rever notas herdadas na V05.
- Alerta documental confirmado: descrição genérica do capital diz «realizado no mês 1», apesar do pipeline faseado. Corrigir a nota; não alterar o calendário para a fazer coincidir com texto antigo.
- A referência de reserva M30 de 3,634 M€ está correta; não deve ser confundida com a caixa M30 de 8,717 M€ ou com uma reserva constante para todos os meses.
- A primeira distribuição M54 ainda não está demonstrada na V05. Será recalculada após retirar distribuições anteriores e aplicar todos os controlos.
- Direitos, lucros legalmente distribuíveis, deliberações, financiamento contratado, fees e avaliação terminal continuam dependentes de documentação externa.
- Não foi inferida bancabilidade só por saldos positivos ou por uma avaliação de saída elevada.

## 8. Testes executados e limites

Executados nesta Fase 1: inventário integral OOXML, integridade ZIP, igualdade de hash do original e cópia, procura de erros armazenados, reconciliação das 94 frações, nova execução Python dos 180 meses e comparação de 1.800 valores mensais (dívida, desembolsos acumulados, dividendos, caixa, défices, reservas, serviço, juros e desembolsos), mais 14 controlos Executive/KPI. Resultado: zero falhas.

A comparação mensal usa tolerância máxima entre 0,01 € e |valor|×1e-9. Os 14 controlos usam as tolerâncias do teste Executive existente. As comparações confrontam caches da V04 preservada com nova execução do motor Python. Não foi efetuado um novo recálculo LibreOffice integral nesta fase; as regressões completas do Excel Fix anteriores permanecem evidência histórica, não foram reclassificadas como executadas hoje.

Ambiente verificado: openpyxl 3.1.5, SciPy, ReportLab e LibreOfficeDev 26.8 disponíveis. Microsoft Excel Desktop não está disponível. Não se certifica abertura/recálculo no motor Microsoft, Excel Web ou WPS. A ausência de erros armazenados não elimina o risco de diferenças de recálculo nativo.

Na Fase 2: primeiro demonstrar paridade com a V04 com a nova política desligada; depois ligar separadamente cap table, calendário de capital, dividendos e saída, atribuindo cada variação de KPI. Atualizar cenários bancários e de risco, testar suspensão/parcial/mínimo/intermédio/máximo, reservas e ausência de dupla contagem. A cobertura de dividendos não substitui o DSCR.

Fases 3–5: sete ecrãs, PT/EN, navegação, explicações, cenários de operador e saída, impressão e testes finais. Nenhum destes componentes é declarado concluído nesta entrega de diagnóstico.

## 9. Decisão solicitada

Aprovar a execução da Fase 2 com a estrutura V05 expressamente pedida. Validar como hipóteses de implementação: cobertura sobre caixa gerada nos 12 meses anteriores, rateio parcial sobre mínimos por categoria e saída proporcional às participações, sem preferências presumidas. Estes mecanismos ficarão identificados como simulações sujeitas a formalização; não criam direitos jurídicos.

A pausa decorre do próprio mandato recebido: «Após o diagnóstico, solicita a aprovação para executar a Fase 2.» O ficheiro original permanece intacto.
