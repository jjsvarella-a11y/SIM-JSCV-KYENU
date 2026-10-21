# KK-01 V05.1 Executive — correção OOXML e cartão TIR

21/10/2026. Ficheiro: KK01_Modelo_Integrado_V05_1_Executive_Excel_Fix.xlsx.

## Estado da entrega

As violações estruturais identificadas foram corrigidas. A versão é uma candidata corrigida para aceitação no Microsoft Excel Desktop. A abertura nesse programa sem recuperação de conteúdo permanece Pendente de Validação Externa: Excel Desktop não está disponível neste ambiente. Não se declara a compatibilidade nativa certificada nem o incidente encerrado.

A validação anterior de ZIP, fórmulas e LibreOffice foi insuficiente para detetar ordens XML inválidas. Esta correção acrescenta validação por esquemas e testes negativos que reproduzem as violações. Não foi fornecido o XML de reparação do Excel; os defeitos normativos abaixo são causas estruturais aptas a explicar uma reparação, mas não permitem identificar os registos que o Excel efetivamente removeu na abertura observada pelo utilizador.

## Diagnóstico comparativo

A V05 anterior apresenta nove vistas de folha com cinco seleções de painéis. O esquema admite até quatro; há seleções repetidas. A V05.1 herda esses nove defeitos e introduz mais 35 violações: 15 estilos e 20 propriedades de linhas de gráficos. Total: 44 ocorrências em 19 partes. A integridade ZIP, isoladamente, não revela estes erros.

| Componente | Defeito comprovado e correção |
|---|---|
| xl/styles.xml — 15 cellXfs | alignment aparecia depois de protection. CT_Xf exige alignment antes de protection. Reordenados os elementos sem alterar a proteção, as fontes referenciadas ou os formatos numéricos. |
| 9 gráficos — 20 linhas | solidFill aparecia depois de prstDash. CT_LineProperties exige o preenchimento antes do traço. Reordenadas as propriedades, preservando as séries, referências, categorias e dados. |
| 9 vistas dos dashboards | Cinco selection, incluindo panes repetidos. Passam a três seleções distintas: topRight/D1, bottomLeft/A6 e bottomRight/D6. Os painéis congelados e a sidebar mantêm-se. |
| Cores e fundos — robustez visual | 162 cores ARGB normalizadas para alfa FF; 94 fundos sólidos tornados explícitos. São medidas de consistência, não violações de esquema por si mesmas. |
| Cartões TIR — 6 regras de formato | Mantidas as expressões e prioridades. As regras passam a alterar apenas a cor explícita do texto; o fundo branco da célula não é substituído por preenchimentos condicionais. |

## Cartão TIR e consistência visual

O EXEC V05!P8 continua numérico, com valor 7,65%, formato percentual português, alinhamento à esquerda e centralização vertical. O fundo é branco opaco, com foreground/background FFFFFFFF. A cor vermelha assinala TIR inferior à taxa exigida; a condição financeira não mudou. Aplicado o mesmo tratamento às TIR dos dashboards de estrutura e retornos.

Cores com alfa zero e fundos automáticos existiam no ficheiro. A renderização preta observada no Excel pode estar associada à interpretação ou recuperação destes estilos; sem reproduzir o evento no Excel não é possível afirmar qual destes fatores causou o cartão preto. A renderização no LibreOffice da candidata mostra texto vermelho legível sobre branco.

## Preservação financeira e funcional

Comparadas 2.126.479 fórmulas e 2.134.128 valores numéricos existentes, sem alterações. Os 40 KPI centrais têm delta zero. Não foram substituídas fórmulas por constantes, acrescentados financiamentos ou alterados pressupostos.

Mantêm-se 348 folhas, os nove dashboards, 180 meses, cenários fiscais, política de dividendos, simuladores e PT/EN. O workbook, nomes definidos, relações do workbook, desenhos/formas, notas, imagens, hiperligações e validações de dados foram preservados. Não se eliminaram gráficos nem a sidebar. Apenas 19 partes existentes foram modificadas, todas de estilos, vistas ou propriedades gráficas.

| KPI | Antes | Depois | Delta |
|---|---|---|---|
| Gross sales value | 50.656.336,37 € | 50.656.336,37 € | 0 |
| Base future CAPEX | 63.168.000,00 € | 63.168.000,00 € | 0 |
| Peak debt | 18.245.949,67 € | 18.245.949,67 € | 0 |
| Cash M30 | 9.860.218,98 € | 9.860.218,98 € | 0 |
| Cash M42 | 5.493.562,96 € | 5.493.562,96 € | 0 |
| Cash M54 | 5.995.124,82 € | 5.995.124,82 € | 0 |
| Simulated M54 distribution | 2.507.809,30 € | 2.507.809,30 € | 0 |
| New investor IRR | 7,65% | 7,65% | 0 |
| New investor MOIC | 2,67× | 2,67× | 0 |
| Net Equity Value | 102.644.161,83 € | 102.644.161,83 € | 0 |
| New investor NPV | -9.671.683,48 € | -9.671.683,48 € | 0 |

O CSV Comparacao_KPI contém os 40 indicadores, valores e fórmulas antes/depois. A prova JSON identifica os hashes da origem e da candidata. A V05 e a V05.1 anteriores permanecem intactas.

## Testes e alcance

Validadas 470 partes SpreadsheetML/DrawingML abrangidas pelos esquemas: zero violações no perfil documentado. Relações do pacote resolvidas, IDs e índices de estilos verificados, sem erros de fórmula armazenados. Dez grupos de regressão Python aprovados; seis cenários de recálculo nativo no LibreOffice, com 1.224.648 comparações e zero falhas inesperadas, incluindo reconciliação dos 62 motores na Base.

Os seis casos são Base, IVA diferido, dividendos Máximo/Acumulados, juro de 8%, PT/EN e filtro ID 201. Não se afirma que os 35 casos anteriores tenham sido todos repetidos: a preservação de todas as fórmulas e valores é comprovada separadamente.

## Método de validação por esquemas

Esquemas ECMA-376 Transitional obtidos do espelho público QtExcel/ecma-376-5th, acompanhados no pacote com hashes. O perfil respeita xml:space em SpreadsheetML Text, suportado por Microsoft Open XML Text.Space. O espelho tipa t como string simples e rejeita esse atributo; apenas a cópia em memória usada no validador omite o atributo. O ficheiro entregue preserva integralmente xml:space e o texto. Nenhum outro erro de esquema é ignorado.

Foram introduzidos, em cópias de teste, alignment após protection, solidFill após prstDash e cinco selection; o validador rejeitou os três casos. Um teste adicional confirma os dois canais brancos opacos do cartão TIR.

## Limitações e aceitação pendente

Abertura sem reparação, aparência e recálculo em Microsoft Excel Desktop: Pendente de Validação Externa. LibreOffice e validação OOXML não substituem esse teste. O relatório de reparação original do Excel não foi disponibilizado.

A Vista Protegida pode continuar a aparecer em ficheiros descarregados, conforme a política de segurança do Excel. Não foi desativado qualquer mecanismo de segurança. A correção dirige-se aos defeitos de conteúdo; não suprime avisos nem força a abertura de ficheiros inválidos.

A pré-visualização PDF é uma renderização estática dos valores em cache com os pressupostos necessários à formatação condicional; serve para inspeção visual, não como teste financeiro adicional nem certificação Excel.
