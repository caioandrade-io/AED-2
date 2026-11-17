# Projeto 2 - Árvores de Busca (SCC0202)

Implementação em C de índices em disco usando **ABB**, **AVL** e **Rubro-Negra**, com busca simples e complexa por offset nos arquivos de dados.

## Integrantes
- Caio Andrade
- (adicionar colegas)

## Estrutura
```
src/           código-fonte (.c)
include/       headers dos TADs (.h)
dados/         datasets (asteroides + dataset do grupo)
indices/       índices gerados (.idx)
consultas/     arquivos de consulta (KEY|coluna|valor)
resultados/    saídas das buscas
experimentos/  dados das repetições e scripts de análise
relatorio/     relatório em PDF
```

## Compilação
```bash
make
```
Gera o executável `trabalho`.

## Uso

### Indexação
```bash
./trabalho --mode index --reader nasa --input dados/asteroids.csv \
  --tree avl --key year --index indices/ano.avl.idx --limit 0
```
- `--tree`: `abb`, `avl` ou `rubro_negra`
- `--limit 0`: indexa a base inteira

### Busca simples (um índice)
```bash
./trabalho --mode search --reader nasa --input dados/asteroids.csv \
  --index indices/ano.avl.idx \
  --query consultas/anos.txt --output resultados/anos.csv
```

### Busca complexa (dois ou mais índices, união OU)
```bash
./trabalho --mode search --reader nasa --input dados/asteroids.csv \
  --index indices/ano.avl.idx --index indices/sentry.rb.idx \
  --query consultas/multiplas.txt --output resultados/multiplas.csv
```

### Formato das consultas
```
KEY|year|2028
KEY|on_sentry_list|true
```

## Datasets
- **Asteroides (NASA):
- **Dataset do grupo:** CENIPA - Ocorrências Aeronáuticas na Aviação Civil Brasileira 
## Métricas
O programa imprime métricas no formato `NOME=VALOR` (ex: `BUILD_MS`, `ROTATIONS`, `SEARCH_MS`, `FETCH_MS`), usadas na análise experimental.
