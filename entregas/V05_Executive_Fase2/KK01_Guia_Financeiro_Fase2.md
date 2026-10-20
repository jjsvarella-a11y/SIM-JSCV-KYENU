# KK-01 | V05 Executive — Guia Financeiro Fase 2

Base: V04 Excel Fix. Guardar sempre uma cópia antes de alterar cenários. Todos os valores de referência são projeções, não pagamentos comprovados. Os dashboards antigos permanecem para continuidade; a reformulação visual ePT/EN é posterior.

## 1. Onde começar

Abrir V05 Retornos para a síntese. Consultar V05 Config para a política, V05 Dividendos para os180 meses, V05 Blocos para os15 blocos e V05 Fluxos Blocos para os oito vetores de investidores. Os links na linha 3 dos novos separadores permitem navegar. No Excel, também pode usar a caixa de nome ouIrPara com 'V05 Retornos'!A1.

## 2. Repor a referência

Em V05 Config: Base de capacidade=Geração 12M; patamar=Automático; cobertura=1,20; parcial=1; saída=Base; realizar saída=1; políticaV 05=1; composiçãoV 05=1; primeiro mês 54; exigir capital-alvo integral=1. Os interruptores de política/composição são técnicos, não alternativas de direitos aprovadas. Em Pressupostos, preservar cenárioKK-E25, calendárioBase, HotelFavorável, bancoLimite aceitável, linha 30 M€ e feesObjetivoKK 3/3/6.

Não existe macro de reposição. Recuperar uma cópia original da entrega ou selecionar os valores de referência. Alterar um input mantém o motor dinâmico; não escrever sobre fórmulas.

## 3. Dividendos e liquidez

Selecionar Geração 12M para impor cobertura 1,20 × ouAcumulados para analisar separadamente lucros e caixa acumulados. Selecionar um teto de patamar. O modelo reduz para o patamar integralmente suportado; se nem o mínimo couber, parcial=1 permite rateio proporcional aos mínimos. Parcial=0 suspende esse pagamento. Suspenso elimina dividendos ordinários, sem transformar metas em dívida.

Na referência, conferir M30 na linha 34 do Fluxo 180M, M42 na46 e M54 na58. A primeira distribuição simulada é2.630.786,91€ com caixa posterior 11.534.262,02€. No modoAcumulados / Máximo, é4.150.000€ e caixa 10.015.048,93€. Os montantes são cenários alternativos, não cumulativos.

A reserva adicional em V05 Controlo colunaBé um valor de proteção no respetivo mês; não é saída de caixa e não deve duplicar valores já reservados emQ/ARdo motor. Uma obrigação com vencimento futuro deve ser protegida nos meses relevantes até ao pagamento. Não informar apenas o mês do pagamento se a intenção for impedir distribuição anterior. O valor protegido no M180 é também deduzido da saída.

## 4. Documentação e pagamentos

V05 Controlo: colunaC=teto mensal indicado como aprovado;D=deliberação comprovada 1/0;E=pagamento comprovado;F=documento/data. Manter em branco o que não esteja disponível. A referência não contém aprovações ou pagamentos fictícios. V05 Dividendos mostra os três conceitos separadamente.

Estes campos são controlos e reporting, não uma atualização automática de todos os realizados históricos. Não somar pagamento comprovado ao dividendo projetado. Para simular o teto legal documentado, selecionar Documentado em Pressupostos e preencher o teto acumulado correspondente com suporte verificado. As restrições legais, bancárias, fiscais e societárias precisam de confirmação externa.

## 5. Capital e blocos

Consultar 15 blocos em V05 Blocos. O pipeline legado mantém 12 parcelas para preservar a tesouraria da V04. Cinco parcelas pertencem ao mesmoG 02; não são cinco blocos Gold. No calendárioBase, esse bloco aplica 3 M€ noM 3 e2 M€ noM 4. Não alterar quantidades de categorias para inferir direitos societários diferentes sem decisão formal.

Os retornos dos novos investidores consideram as datas mensais de todas as parcelas. O MOIC usa recebido total dividido por capital de cenário. A TIR mensal anualizada é calculada com os vetores 0..180. A colunaXIRRcom datas convencionais utiliza uma base uniforme apenas para comparação matemática; não representa datas contratuais ou realização documental. As TIR históricas individuais dos promotores permanecem indisponíveis.

## 6. Operador e financiamento

Usar os inputs centrais existentes em Pressupostos/Condicoes Operador. Objetivo KK seleciona 3% base+3% sistemas+6% incentivo; Proposta simulada seleciona 4%/3%/10%. Não aplicar todos os fees sobre a mesma base. Comparar EBITDA, CFADS, dividendos e saída depois de recalcular.

Alterar linha/taxa/carência/prazo e comissões nos controlos já existentes. A linha é não revolving: amortizar não repõe disponibilidade acumulada. Limite, utilização acumulada e pico da dívida são diferentes.

## 7. Saída e continuidade

Em V05 Config selecionarPrudente 10 ×,Base 12 × ouFavorável 15 ×. O EBITDA é do Ano 15 do projeto, M169–M180. Realizar saída=0 mantém a exploração sem recebimento terminal. EVestimado não é caixa disponível. A distribuição líquida é40% JSCV,10% JALS,50% novos. As metas TIR e preferências V04 não governam a V05.

Rever custos de transação, dívida, caixa normalizada e compromissos antes de negociar uma saída real. Não somar apartamentos vendidos, dividendos anteriores ou fundos restritos ao preço. O múltiplo é uma hipótese económica, não oferta de compra.

## 8. Conferência e exportação

Verificar estados em V05 Retornos eAUDITORIA; consultar o dicionário e fontes existentes. Os relatórios PDF desta entrega contêm a síntese e os testes. Para imprimir uma folha financeira, ajustar a área de impressão e confirmar a pré-visualização. A configuração definitiva dos sete relatórios executivos pertence à fase visual.

No ExcelDesktop, executar recálculo integral e conferir a referência antes de utilizar em decisão. Esta aplicação não está disponível no ambiente de desenvolvimento; não foi certificada a compatibilidade nativa. Se aparecer erro, conservar a cópia e identificar a primeira célula de origem, sem substituir fórmulas por valores ou zeros.
