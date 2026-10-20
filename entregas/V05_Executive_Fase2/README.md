# KK-01 V05 Executive — Fase 2 financeira

Base exclusiva: **V04 Excel Fix**. Original preservado. Esta entrega atualiza a estrutura para15blocos, dividendos progressivos e saída proporcional; **não é a conclusão da fase visual/bilingue**.

## Abrir

1. Descarregar `KK01_Modelo_Integrado_V05_Executive.xlsx` utilizando **Download raw** no GitHub.
2. Começar pelo separador **V05 Retornos**; depois **V05 Config**, **V05 Dividendos** e **V05 Blocos**.
3. Consultar `KK01_Guia_Financeiro_Fase2.pdf` antes de alterar os inputs.

A referência utiliza25M€de captação projetada, HotelFavorável, bancoLimite aceitável e saídaBase12×. Não são compromissos comprovados. No M54, geração12M/cobertura1,20×suporta2.630.786,91€de distribuição simulada; caixa posterior11.534.262,02€. Acumulados/Máximo é cenário alternativo de4.150.000€, não pagamento adicional.

TIR novos15A8,33%,MOIC2,90×eVPL a12%−8,45M€dependem da saída estimada12×. Mantendo9×para comparação, TIR~7,06% eMOIC~2,45×. Estes resultados não constituem garantia de remuneração, financiamento ou preço de venda.

## Relatórios

- `KK01_Relatorio_Fase2_Reconciliacao.pdf`: alterações, liquidez, ponteV04/V05, condições e limitações.
- `KK01_Relatorio_Testes_Fase2.pdf`: testesPython,20cenários e14riscos auxiliares.
- `KK01_Guia_Financeiro_Fase2.pdf`: inputs, cenários, documentação e leitura dos resultados.
- CSVs eJSONs: reconciliação mensal, impactos e evidências.

A falta acumulada de cobertura do objetivo residencial permanece sinalizada; não foi convertida em garantia ou eliminada com valores fixos. Direitos, lucros distribuíveis e pagamentos reais são separados das projeções.

## Limite de compatibilidade

Recalculado e reconciliado emPython/LibreOffice. **Não há Microsoft Excel Desktop neste ambiente e não se certifica o recálculo nativo Microsoft.** Abrir uma cópia no Excel, selecionar cálculo automático e executarCtrl+Alt+Shift+F9; confrontar os indicadores com o relatório. As fórmulas continuam dinâmicas; as caches são resultados do recálculo externo, não substituições por constantes.

## Reprodução

O pacote de fontes/testes inclui `src/`, `reference/src/`, metadados e requisitos. Extrair para uma pasta de trabalho; criar `original/` e colocar aí a V04 Excel Fix, mantendo o nome original. A cópia original não está duplicada no ZIP para manter a entrega abaixo de40MB; continua disponível na pastaV04_Excel_Fix do mesmo repositório.

```bash
python -m pip install -r requirements.txt
python src/test_python_phase2.py
python src/build_phase2.py
python src/run_sensitivities.py
python src/recheck_precision.py
python src/merge_caches.py
python src/check_structure.py
python src/check_recalc.py entrega/KK01_Modelo_Integrado_V05_Executive.xlsx
```

É necessário `soffice` noPATHpara o recálculo externo. Cada teste usa perfil isolado, cálculo de grupos sem multithreading eOpenCLdesativado. As caches das cópias de teste são invalidadas antes do recálculo. Não executar o teste paralelo com o mesmo perfil de uma aplicação aberta.

Os dados documentados introduzidos no caso de testeDocumentos_M54 são sintéticos e não estão na referência entregue. Os contrafactuais da ponte de impactos não são políticas ativas. Para futuras alterações legítimas de pressupostos, documentar e atualizar os casos de referência; não alterar resultados esperados apenas para fazer um teste passar.

SHA-256 do originalFixed: `be8288ced2494ef31c2dbe1d31d77b8277a0753a1209a8df0a83c3a5d86dcdc0`.
