# KK-01 V05 — Decisões pendentes

21/10/2026. Registo de pré-implementação; nenhuma destas decisões foi aplicada ao motor nesta etapa.

| ID / natureza | Decisão necessária | Proposta de tratamento / evidência | Condiciona |
|---|---|---|---|
| F01 Financeira | Entrada primária, suprimentos ou compra de ações existentes? | Confirmar quanto dos25M entra efetivamente na KK; promotores não aportam automaticamente30M convencionais | Fontes e financiamento |
| F02 Financeira | Datas dos oito blocos | Aprovar datas/parcelas próprias e distinguir previsto/contratado/recebido. Calendário agregado preservado anteriormente serve apenas de comparativo | TIR, caixa e juros |
| F03 Financeira | Recuperação IVA | Escolher prazo base e percentagem, e parâmetros dos cenários parcial/diferido; não inventar uma data de reembolso | Pico de dívida e M30/M42/M54 |
| F04 Financeira | Caixa elegível na saída | Confirmar caixa excedentária, normalização de fundo de maneio e obrigações/reservas transferidas; manter ponte para evitar dupla dedução | Equity Value |
| T01 Fiscal | IVA de construção/fiscalização já incluído? | Confirmar contratos/base líquida; titular do crédito, dedutibilidade e recuperação.15% e100% recuperável são hipóteses do mandato | Todo o módulo IVA |
| T02 Fiscal | IRPC20%, ITI1%, IPI0,1% e demais taxas | Parecer com fontes legais, vigência2026, incidência, sujeito passivo e calendário; não substituir23%/1,5% silenciosamente | Impostos e lucros |
| T03 Fiscal | Resultado tributável e imposto de promoção | Confirmar custo dos imóveis vendidos, depreciação, prejuízos fiscais, ajustamentos e consolidação por entidade | IRPC e capacidade de distribuir |
| T04 Fiscal | Convenção e benefícios dos proprietários | Documento de aprovação por benefício/entidade; estado da candidatura não ativa isenções | Regime aprovado |
| J01 Jurídica | 97 escrituras potenciais e PH | Confirmar autonomia Hotel/MICE/restaurante, atos necessários, pagador e datas;20.000€ PH é estimativa de gestão | Custos e calendário |
| J02 Jurídica | Lucros distribuíveis | Contas, reservas legais, deliberações e covenants; proxy financeira não substitui aprovação legal | Dividendos aprovados/pagos |
| S01 Societária | Direitos dos15blocos | Formalizar40/10/50, taxas como objetivos, parcial proporcional sem prioridade nem acumulação e saída proporcional como hipótese-base | Direitos e documentação |
| C01 Comercial | Frações504/810 e provas de venda | M29 continua provisório; identificar contratos, datas, descontos, encargos de comprador e KK | Recebimentos/ITI/IPI/atos |
| O01 Operacional | Inclusão dos seguros | Obter orçamento/forecast/apólices e marcar YES/NO/PARTIAL; só adicionar custo incremental | CAPEX e OPEX |
| O02 Operacional | Pequena divergência da tabela de seguros | 40,1M×0,35%=140.350€; mais27.150+27.150+15.000=209.650€. Confirmar se se prefere cálculo por taxa ou provisão arredondada140.400/209.700; nada alterado | Orçamento de seguros |
| O03 Operacional | Capital seguro e bases de fees | Reconstrução/reposição documentadas, contrato e bases3/3/6 versus4/3/10; sem marca/contrato presumido | EBITDA/seguros/retorno |
| TÉ01 Técnica | Datas reais e motores de teste | Confirmar data inicial e datas dos investimentos; sem dados usar apenas datas convencionais identificadas, nunca chamar XIRR efetiva | Retornos e compatibilidade |
| TÉ02 Técnica | Identidade e traduções | Fornecer/confirmar logótipo, vermelho institucional e terminologia. Protótipo usa vermelho indicativo, sem afirmar manual de marca | Interface PT/EN |

## Conflito de estado e aprovação

A nova instrução de pré-implementação prevalece para os trabalhos futuros; não invalida a autorização e entrega financeiras já existentes. Não se apaga nem regrava essa entrega. A aprovação agora solicitada é para o âmbito consolidado, incluindo novos módulos fiscais e seguros. Reutilização de código anterior será objeto de revisão.

Decisões sem documentação poderão ser modeladas apenas como cenários explicitamente hipotéticos após autorização. O cenário de benefícios aprovados deve ficar sem benefícios ativos até prova; distribuição efetiva nunca será deduzida de uma simulação.
