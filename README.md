# Mineração de Dados — Custos das Empresas de Transporte (IBGE/PAS)

Projeto da disciplina de Mineração de Dados.

**Equipe:** João Murilo, Levy Porfirio, Emerson Ribeiro e André Wilke

**Base:** IBGE, Pesquisa Anual de Serviços (PAS), Tabela 2653 — custos das empresas de transporte, serviços auxiliares aos transportes e correio, Brasil, 2007–2023, em mil reais.

## Sprint 2 — Pré-processamento

O script `preprocessamento.py` executa as 10 etapas descritas na seção 3.2 do relatório:

1. Leitura e padronização
2. Verificação de valores ausentes, duplicatas e valores negativos
3. Consistência contábil (total = soma dos componentes; Total geral = soma das atividades)
4. Remoção do Total geral (136 → 119 registros)
5. Identificação de valores discrepantes pelo critério IQR (sem remoção)
6. Transformação log(1 + x)
7. Atributos defasados em t−1 (119 → 112 registros)
8. One-hot encoding da atividade
9. Multicolinearidade (VIF)
10. Padronização deixada para o treino (Sprint 3)

### Como executar

```bash
pip install -r requirements.txt
python preprocessamento.py base_sprint1.csv
```

### Saídas (pasta `dados/`)

| Arquivo | Conteúdo |
|---|---|
| `base_limpa.csv` | 119 registros, sem o Total geral e com log(1 + x) |
| `base_modelagem.csv` | 112 registros, 14 preditores e o alvo `log_total` |
| `relatorio_preprocessamento.txt` | Resultado de cada verificação |
