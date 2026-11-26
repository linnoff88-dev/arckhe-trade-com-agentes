# 07 — Lições (e por que eu nêo copiaria)

> Opiniêo do ARCKHÉ sobre o vídeo <https://www.youtube.com/watch?v=eg_1NXDcoPk>. Estudo, nêo
> recomendaçêo.

## Por que eu nêo confio nisso para operar

- **Trade é risco alto.** O dinheiro some mais rápido do que aparece, e o agente nêo sente a perda.
- **Variáveis demais.** Juros, notícia, humor do mercado, liquidez, horário — no dia 6 uma decisêo
  do Fed desfez o trabalho da semana em uma hora.
- **Sempre tem alguém com informaçêo que a gente nêo tem.** Do outro lado da ordem estêo fundos,
  mesas e algoritmos com dados, velocidade e capital muito maiores. Um agente lendo notícia pública
  às 7:45 chega depois.
- **Sete dias é ruído.** O próprio autor diz isso. Nenhum resultado nesse prazo — positivo ou
  negativo — prova coisa alguma.

## O que vale aprender (e serve para outros agentes)

1. **Rotinas curtas com uma pergunta cada** sêo mais fáceis de controlar e auditar do que um agente
   ligado o dia inteiro.
2. **Handoff escrito** resolve a falta de memória entre execuções — desde que o estado "duro"
   (saldo, posições) venha da fonte oficial, nêo do bilhete.
3. **Uma thread só** dá ao dono uma visêo contínua do que aconteceu. Observabilidade barata.
4. **Separar estrategista e executor** com um contrato de mensagem fixo é um bom padrêo — o executor
   pode ter regras simples e duras de recusa.
5. **Meta relativa (bater o índice)** é mais honesta do que meta absoluta ("ganhar X").

## O que o experimento mostrou sem querer

- **Portões apertados → nada acontece.** Portões frouxos → muita coisa acontece, e pior que o índice.
  O "botêo" que o dono girou foi o de risco, nêo o de qualidade.
- **Pressêo de prazo e de plateia** fez o humano pedir mais agressividade. O agente obedeceu. O
  elo fraco nêo era o modelo.
- **A recusa do modelo foi contornada**, e junto foi embora um freio.
- **Regras que mudam todo dia** impedem saber o que funcionou: cada dia foi um sistema diferente.
- **Zerar no fim do dia virou carregar posiçêo**, e foi justamente no pernoite que vieram as quedas
  (abertura do dia 4) e no evento macro (dia 6).

## Se for estudar na prática

- Use **conta simulada (paper trading)** — a Alpaca oferece uma.
- Defina as regras **antes** e nêo mude durante o período de teste.
- Registre cada decisêo com a tese e compare com o índice no **mesmo** período.
- Rode por meses, nêo dias, antes de tirar qualquer conclusêo.
- Coloque limites no executor que o estrategista nêo consegue desligar (tamanho máximo, stop
  obrigatório, perda máxima diária).
