# KK-01 V05 Executive — Relatório de auditoria

21/10/2026. Auditoria técnica e financeira de um modelo de estudo. Estados: Conforme nos testes executados / Alerta / Pendente de Validação Externa.

## Evidência e preservação

Base autoritativa: V04 Excel Fix, SHA-256 be8288ced2494ef31c2dbe1d31d77b8277a0753a1209a8df0a83c3a5d86dcdc0. A entrega financeira anterior foi reutilizada como camada rastreável de alterações sobre a V04; o modelo não foi reconstruído do zero. Os originais e os respetivos hashes foram preservados.

A auditoria Fase1 foi aproveitada:313 folhas,1.485.103 fórmulas,17 gráficos e347 nomes definidos na V04. A Fase2 anterior tinha319 folhas; a versão atual acrescenta os módulos técnicos e os nove ecrãs, preservando as folhas antigas. As contagens atuais e o inventário de relações estão em Testes_Estruturais.json.

## Alterações controladas

Estrutura 15 blocos; oito calendários explícitos; separação de fundos primários e secundários; inventário94 frações único; orçamento por capítulos e EAC/ETC de controlo;10 trimestres derivados do mensal; IVA por saldo e prazo; IRPC por lucro tributável anual e calendário; ITI/IPI por responsabilidade/titularidade; atos/PH; seguros incrementais; cenários de incentivos; reservas antes do sweep e dos dividendos; lucros de estudo com retenção prudencial; saída e retornos; nove ecrãs com dicionárioPT/EN central.

O registo completo de fórmulas antes/depois está comprimido em Registo_Alteracoes_Formulas.json.gz; o resumo por folha está em Alteracoes_por_Folha.csv. O registo da Fase2 anterior é incluído separadamente. A rastreabilidade dos valores literais anteriores permanece nos ficheiros originais e nos manifests.

## Correções encontradas durante desenvolvimento

1. A nova proteção fiscal usava inicialmente o imposto do mês anterior no fecho de draw, deixando uma insuficiência de reserva na abertura. Foi acrescentado controlo prudencial do imposto conhecido no último mês de financiamento, sem escudo dos juros atuais, evitando circularidade. A linha continua não renovável e sem capital fictício.

2. Os cenários auxiliares de atraso de obra exigem a sua própria expressão de conclusão e abertura. O acréscimo fiscal às reservas foi ligado às expressões de cada motor, evitando transportar o M30 global para um cenário de obra prolongada.

3. A geração 12M no primeiro mês com dívida passou a somar diretamente principal, juros e encargos obrigatórios. A versão de desenvolvimento mostrou um cache transitório que omitia juros nesse ponto; a expressão explícita passou na reconciliação.

4. As48 simulações financeiras mantêm os respetivos montantes de capital; não recebem automaticamente os 25 M€ do cenário principal. A saída mantém os direitos fixos aprovados, sinalizando cenários de captação incompleta.

5. A compensação de IVA foi limitada ao crédito elegível e à capacidade de IVA liquidado da própria KK introduzida em V05 IVA Comp. Sem capacidade documentada/previsão, não há compensação automática. O crédito permanece pendente.

6. A base com IVA incluído extrai o imposto antes de apresentar custo económico e repõe o desembolso bruto, evitando adicionar novamente o IVA ao mesmo orçamento.

7. Os prémios operacionais são calculados pelas bases e taxas; a diferença do orçamento indicativo foi resolvida por cálculo dinâmico, sem total fixo. Direitos, taxas e coberturas não foram considerados contratados.

8. O comparativo de retorno a 10 anos passou a deduzir o IRPC por pagar emM120, de forma coerente com a saídaM180. Foram comparados o valor líquido, TIR, MOIC e os 121 fluxos da alternativa10 anos, sem somar duas saídas no mesmo cenário.

9. Os consumidores antigos do imposto de transmissão foram ligados à mesma taxa efetiva suportada pela KK, incluindo custos por unidade, cash sweep e projeções futuras de caixa imobiliária. O antigo1,5% é apenas referência do modo legado desligado; os cenários de benefício ITI foram testados separadamente.

## Testes executados

| Verificação | Resultado |
|---|---|
| Cenários de seletores em LibreOffice | 35 |
| Comparações numéricas nativas/Python | 2993251 |
| Falhas numéricas inesperadas | 0 |
| Erros de fórmula inesperados | 0 |
| Reabertura:62 motores incluindo o principal | Conforme |
| Regressões Python | 10 grupos aprovados; inclui paridade com módulos desligados |
| Excel Desktop / Web / WPS | Não executado; sem certificação |


Os testes nativos alteraram seletores por cliente externo Java/UNO ou por alterações OOXML em cópias privadas, seguidas de recálculo nativo integral. Nenhuma macro foi adicionada ou executada. As simulações Aprovada_Prova_Sintetica e Atos_KK_Sintetico são exclusivamente testes; não representam documentos aprovados. O modelo final mantém regimeGeral, candidaturaEm preparação, prova0 e campos de pagamentos efetivos vazios.

As comparações cobrem os 180 meses: caixa, dívida, juros, draws, serviço obrigatório, sweep, lucros, dividendos, IVA, impostos, seguros e fluxos por bloco. Tolerâncias monetárias: máximo de 0,01€ ou1e-9 relativo; rácios1e-7 absoluto/1e-8 relativo. Valores não finitos são rejeitados. Os snapshots nativos verificam erros de todas as folhas, além dos KPI principais. A alteraçãoPT/EN e o filtroID201 foram verificados no motor nativo.

## Reconciliação e resultados

| Marco | Caixa V04 | Caixa final | Dívida final |
|---|---|---|---|
| M30 | 8.717.152,56 € | 9.860.218,98 € | 2.434.951,38 € |
| M42 | 7.760.803,63 € | 5.493.562,96 € | 0,00 € |
| M54 | 7.758.489,22 € | 5.995.124,82 € | 0,00 € |


As diferenças não foram anuladas por valores fixos. Resultam do calendário de captação revisto, da substituição da fiscalidade simplificada, do IVA e do seu timing, de seguros, IPI/atos, juros, reservas e política acionista. A ponte incremental é sequencial e depende da ordem; inclui contrafactuais apenas para diagnóstico. O ficheiro CSV mensal identifica os movimentos e diferenças face à V04.

## Estados e pendências

| Área | Estado / limite |
|---|---|
| Integridade, reconciliação e propagação testadas | Conforme nos testes executados |
| Tesouraria base | Conforme sob hipóteses de cenário; depende de capital/vendas/linha e prazos fiscais |
| Rentabilidade investidores a 12% | Alerta: VPL negativo |
| Stress combinado | Alerta: défices, quando indicados nas sensibilidades |
| Fiscalidade e Convenção | Pendente de Validação Externa; taxas do mandato, não parecer legal |
| Recuperação IVA6 meses | Hipótese de estudo; não direito ou reembolso confirmado |
| IPI e depreciações | Proxies de bases tributáveis e vida útil; sem mapas fiscais certificados |
| Seguros | Provisões editáveis; inclusão e cotações pendentes |
| 94 frações e escrituras504/810 | IDs/preços preservados; M29 dessas frações não contratualmente confirmado |
| Dividendos e pagamentos | Simulação; aprovação, contas e covenants pendentes |
| JSCV/JALS retorno histórico individual | Custos e datas individuais indisponíveis |
| Excel Desktop | Compatibilidade não certificada |


A IRPC da promoção usa uma alocação de CAPEX por área; a depreciação usa base 40,1 M€/30 anos e deve ser substituída por classes fiscais validadas. Os anos fiscais do projeto e o prazo de pagamento3 meses são convenções, não calendário legal certificado. Custos aduaneiros/selo não quantificados a zero são pendências, não isenções.

A inspeção textual da V04 não identificou uma rubrica explícita de seguros. Isso não prova ausência de inclusão em custos agregados; a inclusão na empreitada/forecast permanece por confirmar e pode ser parametrizada sem duplicar o custo. O reporte da promoção e da operação é exclusivo da KK; impostos da JSCV ou dos investidores não são automaticamente consolidados.

A fiscalidade dos proprietários permanece informativa; taxa zero por falta de parecer não constitui benefício. O rendimento por unidade é rateio de estudo do pool, não contrato individual. A conservação patrimonial mantém FF&E/reposição e respetivos fundos sem repetir FF&E inicial.

Não se conclui validação fiscal/jurídica nem viabilidade incondicional a partir destes testes. Os testes comprovam a execução e a reconciliação da lógica financeira explicitamente parametrizada.
