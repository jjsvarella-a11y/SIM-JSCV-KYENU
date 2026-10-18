# KK-01 V04 — Excel Fix

Correção técnica, sem V05 nem funcionalidades de negócio novas. O ficheiro original foi preservado. Não foram alterados pressupostos, direitos económicos ou resultados financeiros legítimos.

## Download e utilização

Descarregar o XLSX por **Download raw file** no GitHub e guardar localmente antes de abrir. Usar `entrega/KK01_Modelo_Integrado_V04_Excel_Fix.xlsx`, conservando a V04 original separada. Modelo e pacote têm menos de 40 MB cada.

No Excel Desktop: ativar cálculo automático; em Windows usar Ctrl+Alt+Shift+F9 para reconstruir dependências e recalcular. O valor esperado de `KPI!B14` e `EXEC KK01!I7` na referência é **14.883.293,59 €**. Conferir os demais cartões contra o relatório técnico. O ambiente usado neste trabalho não tem Excel Desktop; essa validação nativa **não está certificada**.

O anexo recebido é idêntico à V04 publicada e mantém caches válidas. Não contém o resultado em erro do recálculo Microsoft relatado pelo utilizador. O relatório distingue origens estruturais candidatas, alterações aplicadas e causa-raiz Microsoft ainda por confirmar; não apresenta hipóteses como causas comprovadas.

## Alterações limitadas

- Expressões matriciais do residencial substituídas por auxiliares escalares e COUNTIFS/SUMIFS.
- INDEX com linha zero no SUMPRODUCT de construção substituído por referências explícitas entre endpoints.
- Pico de dívida obtido de somas mensais ocultas BD, mantendo saldo inicial+draw antes de amortizações.
- MINIFS substituída por seleção escalar de15anos para reduzir dependência da versão Excel.
- Recálculo automático/integral ao abrir, sem cálculo iterativo.

Os 15.954 auxiliares técnicos estão ocultos em folhas existentes. Continuam 313 folhas, dashboards, gráficos, validações, filtros, hiperligações e 120 notas KPI. Nenhum resultado foi usado para substituir fórmulas; não foram acrescentados IFERROR para esconder erros. As peças de apresentação foram preservadas do original, sem resave final por LibreOffice.

## Evidência

`entrega/KK01_Relatorio_Tecnico_V04_Excel_Fix.pdf` contém o diagnóstico, os caminhos desde KPI!B14, as correções, os resultados, as limitações e a aceitação nativa ainda necessária.

Registos completos: `Formulas_Corrigidas.json/CSV`, `Formulas_Auxiliares.json`, `Rastreio_Dependencias_KPI_B14.json`, `Reconciliacao_Integral_Original.json` e resultados JSON dos testes. Foram reconciliadas 1.497.359 células numéricas com o original. As tolerâncias e contagens estão no relatório.

## Reprodução no ambiente Python/LibreOffice

Python 3.11+; dependências fixadas em requirements.txt; soffice no PATH. Não requer serviços, macros ou credenciais. As dependências já estavam disponíveis no ambiente utilizado; não foi necessária alteração de configuração da cloud.

Executar na pasta extraída `kk01_v04_excel_fix`:

```bash
python -m pip install -r requirements.txt
python src/compat_patch.py
python src/fix_metadata.py
python src/test_phase1.py
python src/test_phase23.py
python src/test_selectors.py
python src/audit_risks.py validacao/V04_Final/out/V04_Final.xlsx
python src/audit_returns_v04.py
python src/test_executive_fix.py
python src/merge_recalculated_caches.py
python src/test_structure_v04.py
python src/test_compatibility_integrity.py
```

O teste de seletores invalida todas as caches, configura perfil isolado LibreOffice com OOXMLRecalcMode=0 e confronta as fórmulas recalculadas com Python. Os 9 casos podem demorar vários minutos e usar aproximadamente 18 GB de RAM; reduzir max_workers no script para 1 se necessário. O relatório de contagens da primeira passagem com falha não é reutilizado como teste final.

Para reproduzir a reabertura no Linux, com o processo LibreOffice anterior terminado:

```bash
mkdir -p validacao/Reabertura_Final
soffice -env:UserInstallation=file:///tmp/kk01_excel_fix_reopen --headless --convert-to xlsx --outdir validacao/Reabertura_Final entrega/KK01_Modelo_Integrado_V04_Excel_Fix.xlsx
python src/verify_reopen_v04.py
python src/report_excel_fix.py
```

`merge_recalculated_caches.py` copia apenas resultados calculados para caches de fórmulas que continuam presentes. Preserva os XML de apresentação do original e verifica cada número contra a V04 de origem. O ficheiro entregue tem forceFullCalc/fullCalcOnLoad; as caches não dispensam a validação no Microsoft Excel.

Original protegido: `original/KK01_Modelo_Integrado_V04_Recebido.xlsx`, SHA-256 `b812f5b34be8f81575b227295738fe1a8005c8cc21c347d1d678870ed62fc0e2`. Fixtures V03 originais acompanham os testes de regressão. A correção aplica-se a essa origem; não substituir silenciosamente o original por outra versão e assumir que os mesmos resultados de regressão permanecem válidos.
