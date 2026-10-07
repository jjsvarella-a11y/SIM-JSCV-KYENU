# Ações restantes no Power BI Desktop

1. Abra o `SIM_Control_JSCV_Kyenu.pbip` na pasta totalmente extraída, com `.Report` e `.SemanticModel` ao lado. Não abra dentro do ZIP nem use a entrada antiga de Recentes.
2. Em **Transformar dados**, confira a origem de `RAW_ACCOUNTING_FILES`; ajuste a pasta `01_ACCOUNTING` pela interface se o caminho Windows original não existir. Use **Fechar e aplicar** e depois **Atualizar**.
3. Confira as páginas 01–06 e os filtros sincronizados. Selecione JSCV, 2026, Monthly e 2026-03: Revenue deve ser 2.412.322 CVE. Confira KYENU no mesmo período sem receita, sem zero automático. Verifique os rácios e resultado líquido indisponíveis enquanto suas fontes faltarem, e a consolidação pendente enquanto não houver eliminações aprovadas.
4. Confira comparação homóloga, Previous Period mensal/trimestral, Comparison Year e datas customizadas; revise tamanhos de fonte, labels e cores no Desktop. Não considere as páginas validadas apenas por abrirem.
5. Quando as fontes reais opcionais estiverem disponíveis e integradas, em **Transformar dados → Gerir parâmetros** configure `SIM_OperationalRoot` para a pasta de CSV integrada; atualize e confira os erros de integridade e os valores de projeto/contratos/recebimentos. Enquanto as fontes faltarem, deixe o parâmetro vazio.
6. Salve o projeto. Se precisar de arquivo único, use **Ficheiro → Guardar como → Power BI (.pbix)** numa nova versão, preservando o original.
