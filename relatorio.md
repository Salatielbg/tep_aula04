# Relatório de atividade — Diário Escolar MCP

## O que foi pedido
Construí um servidor MCP em Python para o diário da disciplina, com média ponderada (N1=3, N2=3, N3=4) e situações por faixa. Registrei o servidor como `diario` no `opencode.json` e documentei o uso no `AGENTS.md`.

## O que foi feito
Criei o `servidor.py` (135 linhas) com as ferramentas `listar_alunos`, `boletim`, `lancar_nota`, `resumo_turma` e o recurso `diario://regras`, operando sobre `dados/turma.csv` (5 alunos). Configurei o `opencode.json` para rodar com `.venv/bin/python servidor.py` e escrevi o `AGENTS.md` (61 linhas) com fórmulas, situações e comandos de verificação.

## O que falhou
Não houve falha registrada no histórico (`git log --oneline` com 4 commits, sem mensagem de erro ou revert).

## Como foi resolvido
Nada a corrigir, pois não houve erro no caminho indicado pelo histórico.

## Ferramentas de IA
Eu usei o agente OpenCode, durante o desenvolvimento do projeto utilizei modelo Nemotrom 3.5, quanto ao modelo muse-spark-1.3-contributor-free, apenas nesta etapa final de leitura do `git log`, do `git diff --stat` e escrita deste relatório.

## Repositorio do Projeto
https://github.com/Salatielbg/tep_aula04.git