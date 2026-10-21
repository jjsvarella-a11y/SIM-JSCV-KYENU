# KK-01 V05 — Plano definitivo de implementação

21/10/2026 | PRÉ-IMPLEMENTAÇÃO | Novo ciclo sujeito a autorização expressa.

## Base e histórico

Preservar V04 Excel Fix e entrega financeira anterior; reutilizar a auditoria Fase 1 e os testes, sem repetir trabalho já comprovado. Os resultados anteriormente entregues não incorporam o novo pacote fiscal/seguros. O calendário agregado de capital antes preservado não constitui aprovação do calendário de cada um dos oito novos blocos.

## Sequência e dependências

| Etapa futura | Trabalho | Dependência / aceitação |
|---|---|---|
| Portão inicial | Aprovação deste plano e decisões críticas | Nenhuma fórmula operacional alterada antes da autorização |
| Fase 2.1 | Sociedade, origem de fundos e oito calendários; histórico e capítulos/EAC | 15 blocos, 40/10/50; capital KK separado de transações secundárias; histórico4,5M não repetido |
| Fase 2.2 | Dez trimestres derivados dos 30 meses; classificação com/sem IVA | Soma trimestral=mensal; FF&E inicial e contingências não duplicados |
| Fase 2.3 | IVA por entidade; impostos/atos; seguros; incentivos | Fonte, titularidade, base, calendário e inclusão documentados; cenários não aprovados claramente simulados |
| Fase 2.4 | Propagação ao motor não renovável, dívida e tesouraria | Todas as fontes/usos conciliados; identificar défices e reservas insuficientes, sem os esconder |
| Fase 2.5 | Dividendos e lucros; saída/retornos; ponte módulo a módulo | M54 e onze datas; cobertura12M separada de acumulados; saída proporcional como hipótese; datas por investimento |
| Portão financeiro | Entrega e validação da Fase 2 | Reconciliação180M, Python/native e sensibilidades aprovadas antes dos dashboards |
| Fase 3 | Nove ecrãs, navegação, filtros, gráficos e identidade | Mesmo motor; preservar antigos até confirmar substituição |
| Fase 4 | PT/EN global e dicionário | Mudança de idioma sem qualquer efeito financeiro; traduções centralizadas |
| Fase 5 | Auditoria final e documentação | Testes funcionais, impressão e motores de Excel efetivamente disponíveis; limitações expressas |

## Arquitetura de dados

Inventário único de frações + capítulos + pipeline por bloco + operação + parâmetros por entidade → módulos IVA/impostos/seguros → movimentos mensais classificados → motor único de financiamento → reservas/lucros/distribuições → saída e fluxos acionistas → KPI/dicionário/nove ecrãs.

As 48 folhas Calc e 13 famílias auxiliares de risco são dependências do mesmo motor lógico; atualizar a geração das fórmulas e testar a propagação, sem criar políticas divergentes. Listas técnicas e nomes de folhas mantêm-se estáveis. Novo IVA não pode ser apenas uma sobreposição gráfica: tem de afetar caixa, juros e retornos.

## Testes e tolerâncias propostas

Comparar V04, estado inicial V05 e cada alteração isolada: captação, IVA, ITI/IPI/IRPC/atos, seguros, incentivos, dividendos e saída. Reconciliar movimentos mensais a 0,01€ e rácios a 1e-7 absoluto /1e-8 relativo; somas societárias a 1e-10. Explicar diferenças de arredondamento antes de aceitar tolerâncias maiores. Não comparar só caches de KPI.

Testar Operador3/3/6 versus4/3/10; IVA integral/parcial/diferido; IRPC geral/isenção3/5anos como simulação; seguros base/+25/+50%; dividendos mínimo/intermédio/máximo/parcial/suspenso; exit10/12/15; datas de escrituras; juros/carência/desembolsos. Adicionar stress combinado de atraso de capital/vendas, IVA diferido e sobrecusto, para não confundir testes isolados com resiliência conjunta.

Controlos obrigatórios: 94 IDs/100% recebimentos; cap table e capital recebido; EAC=realizado+ETC; IVA inicial+crédito-recuperação=final; ausência de compensação entre entidades; fiscalidade sobre lucro tributável; seguros incrementais; dívida não renovável; identidade de caixa; reserva protegida antes de dividendos; M30/M42/M54; EV menos obrigações e mais caixa elegível uma vez; retornos por fluxos/datas. Erros financeiros descobertos devem ser corrigidos na origem, nunca com resultados fixos.

## Compatibilidade e publicação

Excel Desktop/Web/WPS serão testados apenas se disponíveis. A validação anterior em LibreOffice não certifica Excel Desktop. Preservar fórmulas, validações, nomes, gráficos, notas e links; usar modificações OOXML controladas e manifesto SHA-256. Disponibilizar ficheiros e relatórios no repositório de entregas, com pacote abaixo de40MB quando possível.

Não é proposta uma duração fixa sem resolver âmbito fiscal/documental. Cada portão exige evidência concreta e um estado Conforme / Alerta / Pendente de Validação Externa.
