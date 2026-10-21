# KK-01 V05 — Registo de pressupostos e pendências

21/10/2026. Definido pelo mandato não significa contratado ou realizado.

| Grupo | Classificação | Referência |
|---|---|---|
| 15 blocos/40-10-50/tickets | Definido para estudo; formalização pendente | 3P,2G,10S; captação25M |
| Obra/Hotel/inventário | Referências preservadas | 30 meses;200quartos;MICE1.500;94unidades |
| Capital, banco e vendas | Projetado; compromissos por confirmar | Oito blocos/linha30M não renovável |
| Dividendos e exit | Política de simulação | M54–174;1,20×;10/12/15× |
| Fiscalidade | Hipóteses e parecer pendente | IVA15%;IRPC20%;ITI1%;IPI0,1% |
| Seguros | Provisões sem cotações | 197.400€ obra; operação dinâmica |
| Convenção | Não concedida | RegimeGeral; candidaturaEm preparação; prova0 |
| Datas para XIRR | Convencionais | Início01/11/2026; substituir por datas reais |

## Parâmetros centrais novos

| Parâmetro PT/EN | Valor de referência | Unidade | Estado / limite |
|---|---|---|---|
| Ativar módulos novos / Enable new modules | 1 | 0/1 | Desligar permite ponte para Fase2 anterior. |
| IVA construção/fiscalização / VAT rate | 0.15 | % | Mandato; taxa e dedutibilidade carecem parecer fiscal. |
| Cenário IVA / VAT scenario | Integral | lista | Integral, Parcial, Diferido. |
| Recuperação parcial / Partial recovery | 0.75 | % | Hipótese de stress, não previsão fiscal. |
| Prazo recuperação base / Base recovery lag | 6 | meses | Hipótese de estudo editável; sem data de reembolso contratada. |
| Prazo cenário diferido / Deferred lag | 18 | meses | Hipótese de stress. |
| Parte por compensação / Offset share | 0 | % | Só na mesma entidade KK; remanescente por reembolso. |
| Orçamento construção inclui IVA / Budget VAT-inclusive | 0 | 0/1 | 0: base líquida;1: extrair IVA do orçamento, sem acrescentar imposto de novo. |
| IRPC / Corporate income tax | 0.2 | % | Referência do mandato2026; fonte legal ainda por validar. |
| Pagamento após fecho anual / Tax payment lag | 3 | meses | Hipótese: pagamento três meses após fim do ano do projeto; calendário legal a validar. |
| Base depreciável Hotel+MICE / Depreciable basis | 40100000 | EUR | Estimativa de estudo; confirmar custo fiscal, não valor de mercado nem capital seguro definitivo. |
| Vida útil fiscal / Tax useful life | 30 | anos | Hipótese simplificada; substituir mapa por classes após parecer. |
| Retenção prudencial sobre lucro / Profit retention | 0.05 | % | Hipótese de retenção; não certifica montante da reserva legal. |
| ITI transmissão / Transfer tax | 0.01 | % | Referência geral do mandato; vigência, base e sujeito passivo a confirmar. |
| ITI suportado KK / KK share of ITI | 0 | % | Hipótese comprador100%; alterar se KK suportar contratualmente. |
| IPI propriedade anual / Annual property tax | 0.001 | % | Hipótese geral; valores tributáveis reais pendentes. |
| Base IPI terreno / Land taxable base | 1000000 | EUR | Proxy histórica até abertura; sem valor matricial confirmado. |
| Base IPI Hotel+MICE/restaurante / Operating taxable base | 40100000 | EUR | Proxy conjunta, sem duplicar MICE/restaurante; substituir por matrizes reais. |
| Base IPI não vendidos / Unsold taxable factor | 1 | x preço | Proxy tributável do preço; não equivale a valor matricial. |
| CVE por EUR / CVE per EUR | 110.265 | CVE/EUR | Referência central do mandato. |
| Taxa escritura / Deed fee | 24000 | CVE/ato | Valor convencional; sujeito e tabela legal pendentes. |
| Certidão matricial / Tax certificate | 1500 | CVE/ato | Por apartamento. |
| Certidão predial / Registry certificate | 1500 | CVE/ato | Por apartamento. |
| Propriedade horizontal / Condominium constitution | 20000 | EUR | Estimativa de gestão, não inclui atos adicionais automaticamente. |
| Mês PH / PH month | 27 | mês | Hipótese editável, não contrato. |
| Seguro de obra total / Construction insurance rate | 0.0035 | % | 0,30% CAR+0,05%RC para30 meses; não multiplicar por 2,5. |
| Seguro obra já incluído / Included construction insurance | 0 | % | 0 prudente adicional;1 totalmente incluído; confirmar empreitada. |
| Multiplicador seguros / Insurance stress factor | 1 | x | Sensibilidade1/1,25/1,50. |
| Capital patrimonial indicativo / Indicative insured basis | 40100000 | EUR | Confirmar reconstrução/reposição; não capital seguro certificado. |
| Seguro patrimonial / Property insurance rate | 0.0035 | % | Provisão de estudo, não cotação. |
| Interrupção atividade / Business interruption rate | 0.0015 | % receita | Sobre receita anualizada dinâmica. |
| RC exploração / Operating liability rate | 0.0015 | % receita | Sobre receita anualizada dinâmica. |
| Coberturas complementares / Additional cover | 15000 | EUR/ano | Sem sobrepor coberturas. |
| Seguro operação incluído OPEX / Included operating insurance | 0 | % | 0 prudente adicional;1 já incluído; confirmar forecast. |
| Cenário Convenção / Convention scenario | Geral | lista | Geral; Pretendida; Aprovada. Aprovada não ativa sem prova. |
| Estado candidatura / Application status | Em preparação | lista | Estado informativo; nunca ativa benefícios. |
| Benefícios documentados / Documentary approval | 0 | 0/1 | Só ativar com documento válido identificado na colunaE. |
| Anos isenção pretendida / Proposed exemption years | 3 | anos | 3/5; benefício apenas sobre lucro elegível Hotel+MICE como hipótese. |
| IRPC posterior pretendido / Proposed later rate | 0.1 | % | Hipótese de estudo; não benefício concedido. |
| Redução ITI / ITI relief | 0 | % | Dependente de norma e titular. |
| Redução IPI / IPI relief | 0 | % | Não extensível automaticamente a proprietários. |
| Base importações elegíveis / Eligible import base | 0 | EUR | Sem lista de importações: zero significa não quantificado. |
| Direitos aduaneiros / Customs rate | 0 | % | Sem classificação: zero significa pendente, não isenção. |
| Redução direitos / Customs relief | 0 | % | Cenário pretendido ou aprovado com prova. |
| Mês direitos / Customs month | 18 | mês | Hipótese de calendário. |
| Selo financiamento / Financing stamp duty | 0 | % linha | Base e taxa pendentes; despesa só no primeiro desembolso. |
| Selo seguros / Insurance stamp duty | 0 | % prémio | Base e taxa pendentes. |
| Redução selo / Stamp relief | 0 | % | Nunca ativo no regime geral. |
| Taxa proprietário / Owner tax rate | 0 | % | Não quantificado sem parecer; zero NÃO certifica isenção. |
| Custos adicionais proprietário / Additional owner costs | 0 | % rendimento | Só custos ainda não abatidos no pool. |
| Data inicial de estudo / Study start date | 46327 | data | 01/11/2026: convenção editável, não cronograma contratual. |
| Usar calendário8 blocos / Use8block schedule | 1 | 0/1 | 1: calendário próprio revisto de estudo;0: calendário anterior para reconciliação. |
| Proteger imposto no último draw / Protect tax at last draw | 1 | 0/1 | Reserva prudente sem escudo de juros no último mês de crédito; evita deixar obrigação conhecida sem funding na abertura. |

## Pendências materiais

Parecer fiscal com vigência e entidade; bases e depreciações; mapa de importações/selo/taxas; prazo de IVA; período fiscal e liquidação IRPC; contratos e inclusão dos seguros; responsabilidades em 97atos potenciais; regime dos proprietários; escrituras504/810; formalização societária; datas/custos históricos dos promotores; compromissos efetivos de capital/banco/vendas; regras de venda e caixa normalizada na saída.

Zeros em impostos não quantificados, pagamentos ou documentos não demonstram isenções, ausência de obrigações ou realização de caixa.
