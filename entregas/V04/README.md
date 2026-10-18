# KK-01 V04 — entrega auditável

Evolução incremental da V03. Hotel 200 quartos + MICE, residencial 94 frações e fluxo integrado180M. Referência:25M€previstos, JSCV40%/JALS10%/novos50%,20blocos2P3G15S. Não existem dados novos de execução inventados.

## Abrir e descarregar

No GitHub, abrir o ficheiro e escolher **Download raw file** (ícone de descarga). Guardar localmente antes de abrir. O Excel e o pacote completo têm menos de40MB cada; verificar tamanho e SHA-256 no manifesto. O ficheiro de trabalho é `entrega/KK01_Modelo_Integrado_V04.xlsx`. O PDF executivo é estático e não substitui o Excel.

## Utilização

1. Guardar uma cópia. Abrir em Excel e ativar o cálculo automático.
2. Começar em EXEC KK01; seguir os ícones e atalhos nativos.
3. Editar células azuis em Pressupostos e calendários. Registos documentados ficam em branco até existir prova.
4. Selecionar explicitamente o motor Pricing para substituir preços de origem; não interpretar como alteração de contratos.
5. Selecionar calendário, CP, elegibilidade e natureza dos fundos. Venda secundária e transferência à KK são operações distintas.
6. Atualizar realizado documentado, depois rever o plano futuro/ETC e ativar a revisão ETC quando aprovada. Os registos documentais não substituem automaticamente toda a previsão de tesouraria; o modelo distingue dados e cenários.
7. Recalcular integralmente (Ctrl+Alt+F9 no Excel). Rever primeiro caixa, reservas, dívida, DSCR e Completion; depois retornos.
8. A waterfall é proposta não aprovada. O modo Proxy prudente de dividendos é diagnóstico económico e não apuramento legal de lucros. Para decisão de distribuição usar Documentado com teto aprovado; sem teto, dividendos são zero.
9. No horizonte10A aplica-se a política15Aselecionada. Bases10/5/1M€dos promotores são convencionais, não aportes novos. TIR efetiva individual dos promotores exige custos/datas próprios ainda não fornecidos.

## Ambiente e reprodução

Python3.11+, dependências em requirements.txt, LibreOffice/soffice no PATH. Não são necessários serviços, credenciais, macros ou plugins para calcular. O ambiente já dispunha das dependências; não houve alteração de configuração de cloud necessária.

Executar a partir da pasta extraída `kk01_v04`:

```bash
python -m pip install -r requirements.txt
python src/test_phase1.py
python src/test_phase23.py
python src/build_model.py
python src/v04_patch_finance.py
python src/patch_compat_v04.py
python src/patch_draw_dependencies_v04.py
python src/test_selectors.py
python src/audit_risks.py validacao/V04_Final/out/V04_Final.xlsx
python src/audit_returns_v04.py
```

`build_model.py` gera fórmulas; as caches só são válidas depois do recálculo externo. `test_selectors.py` invalida todas as caches, usa perfil LibreOffice isolado com OOXMLRecalcMode=0, recalcula e compara. O teste completo pode demorar vários minutos e usa até3processos e cerca de18GB de RAM; reduzir max_workers para1em máquinas menores. Não executar migrações históricas `upgrade_*`, `finalize_v02.py`, `finalize_v03.py` ou `package_v03.py` sobre a V04.

Para reproduzir a apresentação final, copiar o output recalculado do caso de referência para `entrega/KK01_Modelo_Integrado_V04.xlsx`, depois:

```bash
python src/finalize_notes_v04.py
python src/presentation_labels_v04.py
python src/test_structure_v04.py
python src/export_exec_v04.py
python src/reports_v04.py
```

Os scripts de publicação não enviam automaticamente commits. Os scripts históricos foram preservados como rastreabilidade e contêm nomes de versões anteriores; usar apenas os comandosV04acima. `original/v03/src/engine.py` e `source.json` são fixtures de regressão. As versõesV01,V02,V03publicadas não são alteradas.

## Evidência e limites

Testes Python, seletores, riscos integrados, retornos10/15A, Completion, fórmulas, navegação, notas e integridade constam dos JSON e do relatório de auditoria. Relatórios financeiros leem caches do Excel entregue. Excel Desktop não está disponível no ambiente e não foi testado. Recálculo/reabertura realizados com LibreOfficeDev26.8; OOXML e compatibilidade de funções inspecionados. Validar também no Excel Desktop antes de utilização contratual.

Recursos firmes, orçamento aprovado/realizado, CP/garantias, HMA, leaseback, lucro distribuível, escrituras504/810 e direitos especiais carecem de validação externa. A cobertura projetadaM24não é prova de financiamento assegurado. Os stress mostram insuficiência de reservas e/ou DSCRbaixo. VPL novos a12%é negativo na referência. Não existem retornos, recompras ou liquidez garantidos.

A primeira passagem dos seletores detetou um ramo MINIFS sem prefixo OOXML e uma subtração de TIR indefinida. O JSON `Testes_Seletores_Primeira_Passagem_V04.json` preserva essa falha já corrigida; o estado vigente está em `Testes_Seletores.json` e `Testes_Correcao_Compat.json`. Testes finais:34casos Python,9seletores Excel/Python,14riscos integrados,retornos10/15A eCompletion,29controlos estruturais e16.920recebimentos individuais. Evidência detalhada em cada resultadoJSON.

A reconciliação final dos riscos também detetou que a avaliação de SUM(T:V) no cálculo do primeiro desembolso em dois blocos não refletia todos os fees no recálculo externo. A expressão foi substituída por referências explícitas T+U+V, economicamente equivalentes, seguida de recálculo e comparação integral. Não foram introduzidos valores fixos para corrigir resultados.
