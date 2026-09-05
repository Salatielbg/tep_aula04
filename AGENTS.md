# AGENTS: aula04 — Diário Escolar MCP

## Quick start

```bash
# Run the MCP server (registered as "diario" in opencode.json)
python -m mcp run   # or use the opencode config: .venv/bin/python servidor.py

# Or via the project's own entrypoint:
.venv/bin/python servidor.py
```

## Data

- **CSV**: `dados/turma.csv` — columns: `matricula, nome, n1, n2, n3`
- Weights for weighted media: N1=3, N2=3, N3=4
- Media formula: `round((n1*3 + n2*3 + n3*4) / 10, 2)`
- Empty any of n1/n2/n3 → media = `None` → situacao = `incompleto`

## Situations (media thresholds)

- `aprovado`: media >= 7.0
- `exame`: 5.0 <= media < 7.0
- `reprovado`: media < 5.0
- `incompleto`: any grade missing

## Available tools (MCP resources/tools)

| Tool | Signature | Description |
|------|-----------|-------------|
| `listar_alunos()` | — | Lists all students with grades, media, situacao |
| `boletim(matricula: str)` | — | Individual student boletim |
| `lancar_nota(matricula: str, avaliacao: int, valor: float)` | avaliacao ∈ {1,2,3}, 0≤valor≤10 | Overwrites a grade; returns updated media/situacao |
| `resumo_turma()` | — | Class summary: counts by situation, overall media, histogram |
| `regras()` | — | Calculation rules text resource |

## Commands (high‑signal)

```bash
# List all students (MCP tool call)
python -c "from servidor import listar_alunos; print(listar_alunos())"

# Launch a grade for student 2024001, avaliacao 1, value 9.5
python -c "from servidor import lancar_nota; print(lancar_nota('2024001', 1, 9.5))"

# Turma summary
python -c "from servidor import resumo_turma; print(resumo_turma())"
```

## Testing / verification

- The `opencode.json` registers the `diario` MCP server locally.
- No separate test suite exists; verification is done by calling the tools above or via an MCP client.
- To reset data, edit `dados/turma.csv` directly.

## Constraints / quirks

- `lancar_nota` overwrites the previous grade for that avaliacao (does not average).
- Grades are stored as formatted strings with one decimal (`f"{valor:.1f}"`).
- Media is `None` if any grade is empty string `""`; situacao then `incompleto`.
- The server process must be running (or invoked via `.venv/bin/python servidor.py`) for MCP tool calls to work.