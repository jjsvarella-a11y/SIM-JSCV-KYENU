# KK-01 V05.1 Executive — refinamento visual

21/10/2026. Atualização de apresentação sobre a V05 Executive final, sem alterações aos pressupostos económicos ou à estrutura acionista.

## O que mudou

- Identidade tipográfica KK-01, sem apresentar um logótipo oficial inexistente.
- Sidebar em azul escuro, nove acessos numerados, painel ativo em dourado e ligação ao seletor global de idioma.
- Hierarquia de títulos, labels, valores e notas; cartões claros sobre fundo suave, alinhamento e espaçamento consistentes.
- Executive Overview com os oito indicadores anteriores e quatro novos cartões de apresentação: pico da dívida, Equity Value de saída, exposição máxima de IVA e VPL do projeto. Os valores são referências diretas ao dicionário existente.
- Comentário executivo ligado aos resultados: comparação da TIR com a taxa exigida, distribuição M54 com o objetivo mínimo das categorias e alertas da grelha de sensibilidades.
- Gráficos reposicionados e uniformizados. Séries, referências e dados preservados.
- Guia de leitura por KPI, definições, interpretação, leitura desejável, fonte e ligação ao Dicionário de KPIs. Navegação de ida e volta para o Overview e para o dicionário central.
- Notes dos indicadores e instruções de utilização dos inputs enriquecidas. Painéis congelados mantêm as três colunas laterais e as cinco primeiras linhas.

## Idiomas e comportamento

A navegação, títulos e labels de KPI continuam ligados ao seletor global PT/EN. Mantêm-se as notas e estados que já eram bilingues. O novo guia detalhado, os painéis de leitura, o comentário executivo e as Notes enriquecidas estão prioritariamente em inglês, conforme autorizado, para evitar traduções parciais ou inconsistentes. As descrições de origem dos motores mantêm os identificadores técnicos existentes.

A navegação usa hiperligações nativas: cada destino abre a sua folha com o mesmo enquadramento lateral e o item selecionado destacado. Não existe substituição de conteúdo dentro de uma única folha, nem código/macros. A sidebar fica fixa durante o deslocamento para a direita; os seus itens mais baixos podem sair da vista durante um deslocamento vertical, pois congelar as 46 linhas impediria a leitura útil dos detalhes.

As Notes clássicas do Excel têm limitações de tipografia e não mudam de idioma com fórmulas. O guia visível fornece as explicações formatadas; os títulos de cartões abrem a respetiva entrada. Não foram adicionadas sombras ou efeitos que exijam extensões ou macros.

## Preservação e testes

A V05 original é mantida intacta. Prova_Integridade_Motor_V05_1.json verifica cada fórmula e cada valor numérico já existente por folha/célula, as referências dos gráficos, as imagens, os desenhos VML das Notes e as hiperligações internas. As novas fórmulas são exclusivamente de apresentação e leitura dos motores existentes.

O relatório de testes desta atualização distingue a prova de invariância dos testes nativos de recálculo e navegação. Os 35 cenários financeiros da V05 anterior não são apresentados como se tivessem sido todos repetidos nesta atualização visual.

A compatibilidade com Microsoft Excel Desktop não está certificada: esse programa não está disponível neste ambiente. Os valores são projeções condicionais; esta atualização não converte hipóteses fiscais, dividendos simulados ou avaliações em compromissos aprovados.

## Resultados desta atualização

- As 2.126.466 fórmulas existentes e os 2.134.124 valores numéricos existentes foram comparados com a V05 original, sem diferenças.
- Três casos nativos: Base, PT/EN e filtro ID 201, incluindo verificações dos quatro novos cartões e do comentário executivo.
- Os 62 motores foram reconciliados a partir de snapshots de recálculo nativo; não houve reabertura de um novo XLSX exportado para este teste final.
- As últimas correções de dimensões, áreas clicáveis e notas foram verificadas por igualdade de todas as fórmulas e valores numéricos face à cópia usada no teste nativo. O JSON de prova identifica os dois hashes.
- 40 entradas de leitura de KPI; 112 Notes de indicadores/dicionário enriquecidas e 828 notas de utilização estendidas.
- As ligações laterais usam áreas clicáveis transparentes em formas nativas, para evitar texto azul pouco legível sobre o fundo escuro. Não usam macros.
- A pré-visualização PDF contém os nove painéis. Foi renderizada no LibreOffice a partir de uma cópia estática dos valores em cache, destinada apenas à inspeção visual; não é evidência adicional de recálculo financeiro.

Comparações nativas/Python: 1,185,805; falhas financeiras: 0; erros inesperados: 0.
