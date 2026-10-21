# KK-01 V05 Executive — entrega final

Data: 21/10/2026. Modelo integrado de 180 meses, nove ecrãs executivos, interface PT/EN, estrutura aprovada de 15 blocos e módulos fiscais/seguros. A V04 Excel Fix original permanece intacta.

## Downloads

- [Excel financeiro](KK01_Modelo_Integrado_V05_Executive.xlsx)
- [Relatório de auditoria PDF](KK01_V05_Relatorio_Auditoria.pdf)
- [Relatório executivo PDF](KK01_V05_Relatorio_Executivo.pdf)
- [Guia de utilização PDF](KK01_V05_Guia_Utilizacao.pdf)
- [Documentação e testes ZIP](KK01_V05_Documentacao_e_Testes.zip)
- [Fontes de cálculo e regressão ZIP](KK01_V05_Fontes_e_Testes.zip)

O Excel tem menos de 40 MB. Descarregue o ficheiro e abra a cópia local; a visualização web pode não suportar este volume de fórmulas. O pacote de documentação é separado para também ficar abaixo de 40 MB.

## Resultado e estado

35 cenários nativos aprovados, três verificações finais de interface e reconciliação dos 62 motores: 2.993.251 comparações, zero falhas ou erros inesperados. Há ainda dez grupos de testes Python. A inspeção estrutural e a comparação final do próprio ficheiro constam dos JSON de evidência.

No cenário de referência: caixa M30 9,86 M€, M42 5,49 M€, M54 6,00 M€ após distribuição simulada de 2,51 M€. O objetivo mínimo de 3 M€ não é integralmente atingido no M54. TIR dos novos investidores a 15 anos 7,65%; MOIC 2,67×; VPL a 12% −9,67 M€. Estes resultados dependem das hipóteses e da saída estimada, não de preço de venda contratado.

Os testes de cálculo não certificam a viabilidade incondicional. Microsoft Excel Desktop não está disponível: a compatibilidade nesse programa não está certificada. Questões fiscais, contratos, calendário de capital e aprovação legal de dividendos permanecem identificados nos relatórios.

O modelo inclui fórmulas dinâmicas e caches recalculados; não contém macros. Inputs azuis estão desbloqueados. As folhas novas têm proteção sem palavra-passe para evitar alterações acidentais às fórmulas. Não ordenar as estruturas de configuração/captação.

Registo_Alteracoes_Formulas.json.gz é um registo comprimido por célula, não uma contagem de erros originais. Manifesto_SHA256.json permite verificar a integridade dos ficheiros. Nenhum dividendo simulado equivale a distribuição legalmente aprovada ou pagamento efetivo.
