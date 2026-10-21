# KK-01 V05 Executive — Guia de utilização

21/10/2026. Abrir KK01_Modelo_Integrado_V05_Executive.xlsx e iniciar em EXEC V05. Trabalhar numa cópia para simulações. O ficheiro mantém fórmulas nativas e não contém VBA.

## Navegação e idioma

A sidebar dos nove ecrãs abre qualquer painel; o rodapé permite regressar à Visão Executiva e consultar fontes. O nome técnico DASH02 identifica exclusivamente Fiscalidade, Incentivos e Seguros. Os painéis antigos continuam disponíveis, identificados como legado.

Selecionar PT ou EN em CONFIG_LANGUAGE!B5. É um único controlo global: menus, títulos, cartões, legendas e avisos consultam DIC_TRANSLATIONS. A mudança de idioma não modifica pressupostos ou resultados. Os nomes técnicos das folhas e códigos de cenários mantêm-se estáveis.

Clicar no título de um KPI para abrir V05 KPI. Consultar definição, unidade, fórmula da célula, fonte e limitações. O V04 Dicionario KPI foi preservado e está ligado pelo novo dicionário.

## Alterar cenários

Células editáveis estão assinaladas a azul com notas. As folhas novas protegem fórmulas sem password; os inputs azuis continuam desbloqueados. Para manutenção estrutural, retirar a proteção na opçãoRever/Desproteger folha e restaurá-la após a alteração. Não ordenar linhas das folhas de configuração, captação ou traduções: as referências são estáveis por endereço. V05 Parametros controla IVA, impostos, seguros, incentivos e hipóteses fiscais. Pressupostos mantém os parâmetros originais da operação, obra, banco e cenários. V05 Config controla dividendos e saída. Os botões da top bar levam às fontes; não existem nove cópias independentes dos inputs.

Com Usar calendário8 blocos=1, editar compromisso/recebimento e parcela destinada à KK em V05 Captacao. Os meses próprios substituem o calendário legado. Para testar os antigos calendários Base/Acelerado/Prudente/V03, usar seletor0 e o controlo original em Pressupostos. A origem do capital deve distinguir primário, secundário ou empréstimo; não editar percentagens societárias para ajustar artificialmente o funding.

O calendário-base revisto recebe P01 noM1, G01 noM2, G02 noM3, S01 noM4, S02/S03 noM5 e S04/S05 noM6. G02 mantém cinco parcelas técnicas simultâneas de 1 M€, agregadas num único bloco5 M€. É hipótese de estudo, não contrato.

IVA: Integral é100% recuperável com lag6 meses de estudo; Parcial usa percentagem editável; Diferido usa18 meses editáveis. Crédito não recuperável integra o custo económico; crédito pendente não é caixa. Compensação exige capacidade mensal da mesma entidade em V05 IVA Comp. Não transferir créditos de outras sociedades.

Convenção: Geral não tem benefícios; Pretendida simula propostas; Aprovada só pode ativar benefícios com estadoAprovada, prova1 e identificação do documento. O estado de candidatura isolado não altera impostos. Não confundir o ensaio sintético dos testes com aprovação efetiva.

Seguros: indicar fração incluída na empreitada/OPEX entre0e1. O modelo acrescenta apenas o remanescente. O fator1/1,25/1,50 testa prémios. Os seguros de obra197.400€ correspondem à obra inteira30 meses, sem multiplicação por 2,5 anos.

## Construção, atos e titularidade

V05 Capitulos apresenta orçamento, contratado, realizado, ETC e EAC. Valores documentais não fornecidos ficam vazios. O ETC calculado pode ser revisto, mas a aplicação ao motor mantém o controlo central de ETC/EAC em Pressupostos/V04 EAC; não ativar duas revisões do mesmo custo. Confirmar coerência entre o mapa por capítulos e o override central antes de uma revisão de orçamento.

V05 Trimestres agrega o motor mensal; os primeiros dez trimestres correspondem aos 30 meses-base. Em atraso, custos adicionais podem ocorrer nos trimestres seguintes e não devem ser truncados para forçar reconciliação.

O inventário único e o calendário das94unidades continuam em Unidades. V05 Escrituras consulta esse calendário e permite definir quota de custos suportada pela KK, outros encargos e os três atos não residenciais potenciais. PH é provisão separada20.000€ noM27 de estudo. Não imputar custos dos compradores à KK por defeito.

## Filtros comerciais

Nos DASH04A/04B, os filtros de ID, tipologia, piso, mês e trimestre atuam no detalhe e no gráfico associado. Todos desativa a restrição. O ID aceita entrada manual como201. Os cartões globais de tesouraria continuam a representar o projeto. Estes filtros não alteram o pricing nem o calendário financeiro; para alterar o cenário editar a fonte em Unidades/Pressupostos.

## Dividendos, saída e retornos

Primeira data elegívelM54; seguintes cada12 meses atéM174. M180 tem apenas saída, sem ordinário adicional implícito. A base usa caixa gerada nos12 meses anteriores com cobertura1,20×, caixa protegida e lucro de estudo. Acumulados é uma análise independente; pode suportar um montante com cobertura12M inferior ao limite e deve ser lida como alternativa.

Quando o mínimo 3 M€ não é suportado, o cenário parcial distribui proporcionalmente aos objetivos mínimos das categorias. Não há prioridade adicional ou dívida automática por dividendos não pagos. V05 Controlo distingue valores documentados, aprovação e pagamentos efetivos; deixar vazio quando não houver prova. Os registos documentais não criam um segundo desembolso no forecast.

A saídaM180 usa EBITDA dos meses169–180 e múltiplo10/12/15×. Deduz custos, dívida e obrigações, incluindo IRPC por pagar; adiciona caixa elegível uma vez. Os proprietários dos apartamentos já vendidos não entram como ativos próprios no EV. JSCV/JALS/novos recebem40/10/50 da saída como hipótese-base de estudo.

As TIR mensais são anualizadas sobre fluxos de cenário. A XIRR utiliza datas convencionais editáveis, ancoradas em 01/11/2026 como hipótese; não é TIR histórica efetiva sem datas reais. MOIC inclui saída hipotética. Os promotores não têm custo de entrada individual documentado; não interpretar os tickets convencionais como capital novo ou investimento histórico efetivo.

## Alertas e compatibilidade

Consultar défice de caixa, reserva, DSCR, cobertura dos dividendos e rácios do operador. O DSCR exclui sweep voluntário e apresenta a cobertura operacional do serviço obrigatório; durante a construção os encargos são analisados pelas fontes e usos. Rácios do operador usam CFADS consolidado KK após impostos pagos e antes de dívida, explicitando meses sem caixa positiva.

Não editar fórmulas ou valores de saída para apagar alertas. Um teste técnico aprovado não torna viável um cenário com funding ou reservas insuficientes. O Excel deve estar em cálculo automático; ao abrir efetuar recálculo integral se necessário. Não foram realizados testes em Excel Desktop/Web/WPS: LibreOffice e Python são os motores efetivamente utilizados.
