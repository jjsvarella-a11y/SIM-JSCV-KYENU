# KK-01 V04 | Correção de compatibilidade Excel

2026-10-18T16:39:17.795930+01:00

Correção técnica restrita à V04. Não foi iniciada uma V05, não foram acrescentados módulos de negócio e não foram alterados os pressupostos ou os resultados económicos legítimos. O original recebido foi preservado integralmente. Este relatório distingue evidência confirmada, alterações preventivas e validação ainda pendente no Microsoft Excel.

## 1. Conclusão e limitação de aceitação

O ficheiro corrigido passou no recálculo pelo LibreOffice e nas regressões financeiras, incluindo os 180 meses e os KPI do Executive Control Center. Foram comparadas 1.497.359 células numéricas com a V04 original, sem diferenças acima da tolerância. As fórmulas continuam dinâmicas; não foram substituídas por resultados fixos.

Não existe Microsoft Excel Desktop neste ambiente Linux. Por isso, não se certifica que o erro comunicado foi reproduzido e eliminado no motor Microsoft. A causa-raiz específica no Excel permanece por confirmar experimentalmente. O anexo contém caches válidas e é byte-idêntico ao ficheiro publicado, sem guardar as células com #VALOR! do recálculo observado pelo utilizador. A ausência de erros em cache não foi usada como prova de compatibilidade Excel.

| Critério | Estado / evidência |
|---|---|
| Original preservado | Conforme — SHA-256 verificado |
| Números e fluxos financeiros | Conforme no ambiente de validação — Python e LibreOffice |
| Fórmulas, interface e rastreabilidade | Conforme nos controlos OOXML e regressões |
| Abertura e recálculo Microsoft Excel Desktop | Pendente — aplicação não disponível |
| Primeira célula efetivamente em erro no Excel | Pendente — não observável no anexo, que mantém caches anteriores |

## 2. Ficheiros e identificação da origem

Origem: KK01_Modelo_Integrado_V04.xlsx, recebido do utilizador. SHA-256: b812f5b34be8f81575b227295738fe1a8005c8cc21c347d1d678870ed62fc0e2. A cópia imutável no pacote chama-se original/KK01_Modelo_Integrado_V04_Recebido.xlsx. A entrega corrigida chama-se KK01_Modelo_Integrado_V04_Excel_Fix.xlsx.

Inventário original: 313 folhas e 1.469.149 fórmulas. Não foram encontrados vínculos externos de workbook, macros ou fórmulas com mais de 8.192 caracteres. Não havia calcChain no original; não foi identificada uma cadeia armazenada inválida. As funções e os tipos foram inventariados em Inventario_Compatibilidade.json. O recálculo anterior em LibreOffice não certificava o Microsoft Excel.

## 3. Rastreio do KPI comunicado

Sintoma comunicado pelo utilizador: KPI!B14. O Executive Control Center mostra este indicador em EXEC KK01!I7. A fórmula original toma o máximo de 180 somas escalares de saldo inicial e desembolso. O rastreio estático expandiu 1.380.723 referências e alcançou 37.349 células com fórmulas. Não foram detetados erros armazenados nessa cadeia.

Foram localizadas 900 células candidatas a diferenças de avaliação matricial na cadeia principal: 540 no perfil de CAPEX e 360 no residencial. São origens estruturais candidatas, não primeiras células de erro comprovadas no Excel. Os caminhos abaixo seguem as dependências desde B14 até às fórmulas de origem; os erros, se produzidos no motor Microsoft, propagam no sentido inverso.

KPI!B14 → Fluxo 180M!X5 → CAPEX!E5 → V04 CAPEX Base!E5 → V04 CAPEX Base!B5

KPI!B14 → Fluxo 180M!X5 → Fluxo 180M!Q5 → Residencial!U5 → Residencial!S5 → Residencial!K5 → Residencial!D5

KPI!B14 → Fluxo 180M!X5 → Fluxo 180M!Q5 → Residencial!U5 → Residencial!S5 → Residencial!O5 → Residencial!M5 → Residencial!L5

Rastreio_Dependencias_KPI_B14.json contém os caminhos e as fórmulas completas. Sem um ficheiro que guarde os erros após recálculo no Excel, ou sem acesso ao próprio Excel, não seria rigoroso declarar uma dessas células como causa-raiz experimentalmente confirmada.

## 4. Fórmulas corrigidas e fundamento

| Classe de alteração | Quantidade | Tratamento |
|---|---|---|
| Residencial: IF sobre intervalos dentro de SUMPRODUCT | 6.120 | Datas e preços por fração em referências escalares; COUNTIFS/SUMIFS |
| Construção: INDEX com linha zero dentro de SUMPRODUCT | 1.080 | Intervalo explícito entre dois INDEX com linhas escalares |
| Pico de dívida: MAX de 180 somas | 63 | Somas mensais ocultas e MAX de intervalo |
| DSCR: _xlfn.MINIFS | 1 | MIN de 15 IF escalares, com a mesma seleção de anos |

Total: 7.264 fórmulas existentes reescritas e 15.954 fórmulas técnicas auxiliares adicionadas em colunas ocultas de folhas existentes. Permanecem 313 folhas. Os auxiliares não constituem novas funcionalidades: tornam explícitas operações que já existiam. O ficheiro final contém 1.485.103 fórmulas.

## 4.1 Residencial — avaliação escalar por fração

Antes, receita e yield alvo dependiam de SUMPRODUCT com IF e operações sobre intervalos de 94 linhas. Este padrão pode ser avaliado de forma diferente conforme a versão e o contexto matricial. Não se afirma que todo SUMPRODUCT com IF seja inválido no Excel; o risco identificado é a dependência de avaliação matricial implícita sem uma fórmula matricial OOXML explícita.

Em cada uma das 17 folhas residenciais, AA5:AA98 calcula o mês de venda, AB5:AB98 calcula a escritura efetiva e AC5:AC98 referencia o preço. Cada auxiliar usa uma única fração. As fórmulas conservam os mesmos atrasos, limites de novas vendas, disponibilidades físicas, preços e cláusulas de elegibilidade do original.

Depois, o número de frações disponíveis usa COUNTIFS sobre AA e AB; o preço elegível usa SUMIFS sobre AC com os mesmos critérios. Exemplo de núcleo: COUNTIFS($AB$5:$AB$98,"<="&A5,$AA$5:$AA$98,"<="&Pressupostos!$B$139). Mantêm-se os multiplicadores de ADR, ocupação, noites e demais parâmetros. A yield não foi garantida ou aumentada.

## 4.2 Construção — referências explícitas

A expressão INDEX(matriz,0,coluna) devolve uma coluna matricial. Foi substituída, dentro de SUMPRODUCT, por INDEX(matriz,1,coluna):INDEX(matriz,30,coluna). Assim o segundo argumento é uma referência explícita ao intervalo de 30 capítulos. Não se alteraram os pesos, os montantes, os fatores, os atrasos ou a realização da contingência. A expressão antiga pode ser válida no Excel moderno; esta mudança reduz a ambiguidade sem mudar a operação económica.

## 4.3 Pico de dívida — célula reportada

Nas 62 folhas de fluxo, BD5:BD184 contém O5+X5, O6+X6, etc.: saldo inicial mais desembolso antes das amortizações. A implementação de KPI!B14 passou a MAX('Fluxo 180M'!$BD$5:$BD$184). Comparativos e riscos usam o mesmo mecanismo. A fórmula original com 180 argumentos está dentro do limite do Excel moderno; a simplificação é uma medida de robustez e auditabilidade, não prova de que MAX era inválido.

## 4.4 DSCR e dependências de recálculo

KPI!B34 usava _xlfn.MINIFS, dependente da disponibilidade dessa função na edição do Excel. Foi substituída por uma seleção escalar dos 15 anos, preservando a distinção entre ausência de serviço obrigatório e um rácio numérico. Os anos não elegíveis usam um valor técnico apenas dentro do mínimo, protegido pela contagem de anos elegíveis; esse valor não é apresentado como DSCR. A alteração também foi testada com serviço de dívida ativo. Esta possível origem de #NOME? é independente da causa comunicada em B14.

Foi configurado cálculo automático, fullCalcOnLoad=1, forceFullCalc=1, calcId=0 e iteração desativada. O objetivo é reconstruir dependências e recalcular no Excel, em vez de confiar nas caches do LibreOffice. Não foram criadas circularidades ou funções de substituição que transformem erros em zeros. Nenhum IFERROR foi acrescentado para esconder erros.

## 5. Preservação do ficheiro e das fórmulas

O ficheiro entregue deriva do OOXML original corrigido. Não se utilizou o save do LibreOffice como ficheiro final de apresentação: transferiram-se apenas as caches de cálculo validadas. Gráficos, imagens, notas clássicas, estilos, tabelas e relações mantêm os mesmos bytes. Hiperligações, validações de dados, filtros, merges, vistas e impressão foram comparados. As entradas e pressupostos não foram alterados.

O dicionário de KPI foi atualizado apenas onde a fórmula técnica mudou. Os comentários continuam a apontar para as mesmas células de origem. Todas as mudanças de fórmulas e todos os auxiliares constam de Formulas_Corrigidas.json/CSV e Formulas_Auxiliares.json; os números fixos em caches não substituem as expressões dinâmicas.

## 6. Testes executados

| Verificação | Resultado |
|---|---|
| Fase 1 financeira Python | 14 testes; 0 falhas |
| Fases 2/3 e operações Python | 20 testes; 0 falhas |
| Seletores reais, recálculo externo e Python | 9 casos; 87.785 comparações; 0 falhas |
| Riscos integrados e waterfall | 14 casos; 166.570 comparações; 0 falhas |
| Retornos 10/15 anos e Completion | 153 comparações; 0 falhas |
| Executive Control Center e DSCR | 126 comparações; 0 falhas |
| Regressão estrutural V04 | 29 controlos; 0 falhas; inclui 16.920 recebimentos individuais |
| Integridade específica Excel Fix | 18 controlos; 0 falhas |
| Todos os números do original | 1.497.359 células; 0 diferenças acima da tolerância |
| Reabertura do ficheiro final | 9.906 valores; 120 notas KPI preservadas; 0 erros armazenados |

Os seletores testados abrangem referência, capital prudente com atraso, atraso da obra/vendas/abertura, CP não cumprida, empréstimo e pari passu, dividendos mensais, teto legal documentado, pricing individual e revisão ETC com comissão de compromisso. Os 14 riscos incluem combinações e linhas 20/25/30 M€. Foram inspecionadas todas as folhas à procura de códigos de erro em cada recálculo. Todos os nove casos terminaram sem códigos de erro inesperados no ambiente de validação.

Tolerâncias: a reconciliação integral usa máximo entre 1e-8 e |valor|×1e-10; os fluxos comparados com Python usam tolerância absoluta de cêntimos ou relativa de 1e-9, conforme o valor. Os KPI têm controlos próprios mais restritos. As caches foram invalidadas antes dos testes de seletores, para não aprovar resultados antigos sem cálculo.

## 7. KPI principais — valores reconciliados

| Célula / indicador | V04 original | Excel Fix |
|---|---|---|
| A7 | Capital KK previsto | 25.000.000,00 € | 25.000.000,00 € |
| E7 | Quota paga equivalente | 50,00% | 50,00% |
| I7 | Pico de dívida | 14.883.293,59 € | 14.883.293,59 € |
| M7 | Utilização acumulada | 19.187.648,01 € | 19.187.648,01 € |
| A12 | Caixa mínima | 3.633.802,73 € | 3.633.802,73 € |
| E12 | Dívida do marco M30 | 0,00 € | 0,00 € |
| I12 | Juros 180 meses | 619.930,36 € | 619.930,36 € |
| M12 | DSCR ano parcial | 2,99 x | 2,99 x |
| A17 | EBITDA: segundo ano operacional | 5.012.848,61 € | 5.012.848,61 € |
| E17 | TIR novos investidores 15A | 7,85% | 7,85% |
| I17 | MOIC novos investidores | 2,48 x | 2,48 x |
| M17 | VPL novos investidores | -8.358.003,30 € | -8.358.003,30 € |

KPI!B14 e EXEC KK01!I7 permanecem em 14.883.293,59 €. A definição e a medição do pico não foram alteradas. A17 conserva a janela do modelo original: segundo ano operacional, M43 a M54 na referência. A comparação não usa o primeiro ano civil completo como substituto dessa definição. Os valores acima são os calculados e reconciliados no ambiente disponível; não são uma medição de recálculo Microsoft Excel Desktop.

## 8. Validação nativa ainda necessária

Ambiente utilizado: Python 3.12.14 e LibreOfficeDev 26.8.0.0.alpha0. Não há Excel, EXCEL.EXE, Wine ou automação COM disponíveis. O código e os resultados deste trabalho não substituem um teste no motor Microsoft.

Procedimento de aceitação no Excel Desktop: abrir uma cópia de KK01_Modelo_Integrado_V04_Excel_Fix.xlsx; selecionar Fórmulas → Opções de Cálculo → Automático; no Windows executar Ctrl+Alt+Shift+F9 para reconstruir dependências e recalcular; verificar KPI!B14 e os 12 cartões contra a tabela; editar a linha bancária para 20 M€ e confirmar reação dos KPI, regressando depois a 30 M€. Na referência de 20 M€, o pico esperado é 14.437.177,18 €. Registar versão/build do Excel e resultados. Este procedimento está documentado, mas não foi executado neste ambiente.

Caso o motor Microsoft continue a produzir erro, a próxima evidência necessária é o endereço da primeira célula em erro durante Avaliar Fórmula ou uma cópia guardada após o recálculo nativo. Isso permitirá distinguir uma diferença residual de função, de tipo ou de contexto. Não se declara compatibilidade certificada nem se apresenta a hipótese de origem como causa confirmada.

## 9. Reprodução e rastreabilidade

O pacote inclui o original recebido, scripts de correção, motores de referência, fixtures, testes, registos completos das fórmulas e manifestos SHA-256. O README contém os comandos de reprodução. A correção é aplicada a uma cópia e o histórico V04 publicado permanece preservado. Não foram modificados direitos acionistas, contratos, condições bancárias, calendário comercial ou premissas operacionais.
