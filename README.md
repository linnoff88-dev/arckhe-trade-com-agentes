# Trade com Agentes â€” o mÃ©todo do desafio de 7 dias

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="48" />
  <p><strong>Arckhé AI</strong></p>
</div>


**ðŸ‡§ðŸ‡· [PortuguÃªs](README.md) Â· ðŸ‡ºðŸ‡¸ [English](README.en.md) Â· ðŸ‡ªðŸ‡¸ [EspaÃ±ol](README.es.md)**

[![Trade com Agentes](guia/assets/banner.jpg)](https://inematds.github.io/trade-com-agentes/guia/)

> ## âš ï¸ Leia antes: isto Ã© um texto de estudo, nÃ£o uma recomendaÃ§Ã£o
>
> **Eu nÃ£o confio nisso para operar.** Trade Ã© risco alto, tem variÃ¡veis demais e **sempre tem
> alguÃ©m do outro lado com informaÃ§Ã£o que a gente nÃ£o tem**. Este repositÃ³rio nÃ£o Ã© conselho
> financeiro, nÃ£o Ã© estratÃ©gia validada e nÃ£o Ã© convite para colocar dinheiro em robÃ´.
>
> O objetivo Ã© outro: **aprender com o que ele fez** â€” como montou os agentes, como passou o
> contexto de um para o outro, onde travou e o que mudou no caminho. O prÃ³prio resultado do
> desafio mostra o ponto: em 7 dias, o sistema **perdeu para o S&P 500**.

## ðŸ“– Guia de uso

Guia completo (landing + passo a passo): **https://inematds.github.io/trade-com-agentes/guia/**

## De onde vem

VÃ­deo no YouTube: **"I Gave GPT 6 Astra $10,000 to Trade Stocks...And This Happened"** â€”
<https://www.youtube.com/watch?v=eg_1NXDcoPk>

O autor deu US$ 10.000 de dinheiro de verdade para um agente no **Codex com GPT-6 Astra
(esforÃ§o alto)** operar aÃ§Ãµes por **7 pregÃµes**, com a meta de **bater o S&P 500**. Diferente de
um teste anterior dele (com OpenClaw, 30 dias, sem mexer), aqui ele podia fazer **atÃ© duas
mudanÃ§as por dia** â€” mas nÃ£o podia desligar o sistema, mesmo perdendo.

Tudo que estÃ¡ aqui Ã© **parÃ¡frase do vÃ­deo**. NÃºmeros sÃ£o **"conforme relatado no vÃ­deo"**; nada
foi auditado. A transcriÃ§Ã£o Ã© automÃ¡tica, entÃ£o alguns nomes podem estar ouvidos errado (ver
[metodo/06-diario-7-dias.md](metodo/06-diario-7-dias.md)).

## O mÃ©todo em uma tela

```
07:45  prÃ©-mercado   â†’ lÃª notÃ­cias, confere conta, escolhe o que vigiar
09:30  1h de pregÃ£o  â†’ procura a primeira entrada que passe nos filtros
11:00  meio do dia   â†’ revisa posiÃ§Ãµes, Ãºltima chance de nova entrada
13:00  tarde         â†’ administra o que estÃ¡ aberto
14:15  fechamento    â†’ encerra as posiÃ§Ãµes restantes
14:45  confirmaÃ§Ã£o   â†’ confere se zerou e registra o resultado do dia
15:15  aviso final   â†’ notificaÃ§Ã£o
(horÃ¡rio Central dos EUA â€” pregÃ£o das 8:30 Ã s 15:00 CT)

Cada rotina acorda â†’ LÃŠ o bilhete de handoff da anterior â†’ age â†’ ESCREVE o prÃ³ximo bilhete.
Todas rodam na MESMA thread: parece um agente sÃ³ trabalhando o dia inteiro.
```

A partir do dia 2 entrou uma segunda peÃ§a: o modelo **se recusou a executar ordens sozinho**.
SoluÃ§Ã£o dele: o Astra vira sÃ³ o **estrategista** e termina cada rotina mandando um **e-mail** com as
recomendaÃ§Ãµes para um **bot executor** (que tem e-mail prÃ³prio + webhook). O bot acorda com o
e-mail e manda a ordem para a corretora **Alpaca**.

## ConteÃºdo

| Arquivo | O que tem |
|---|---|
| [metodo/01-visao-geral.md](metodo/01-visao-geral.md) | Regras do desafio, peÃ§as e arquitetura |
| [metodo/02-rotinas.md](metodo/02-rotinas.md) | As 7 rotinas do dia, uma a uma |
| [metodo/03-handoff.md](metodo/03-handoff.md) | A continuidade: bilhete de passagem entre agentes |
| [metodo/04-estrategista-executor.md](metodo/04-estrategista-executor.md) | Por que separou quem pensa de quem executa |
| [metodo/05-portoes-de-risco.md](metodo/05-portoes-de-risco.md) | Filtros, relaÃ§Ã£o risco/retorno e como foram afrouxados |
| [metodo/06-diario-7-dias.md](metodo/06-diario-7-dias.md) | O que aconteceu em cada dia (nÃºmeros relatados) |
| [metodo/07-licoes.md](metodo/07-licoes.md) | O que dÃ¡ para aprender â€” e por que eu nÃ£o copiaria |
| [templates/rotinas.yaml](templates/rotinas.yaml) | Agenda das rotinas em formato de configuraÃ§Ã£o |
| [templates/handoff.md](templates/handoff.md) | Modelo do bilhete de handoff |
| [templates/prompt-rotina.md](templates/prompt-rotina.md) | Modelo de prompt de cada rotina |
| [templates/recomendacao.json](templates/recomendacao.json) | Formato do e-mail estrategista â†’ executor |

**NÃ£o hÃ¡ cÃ³digo de operaÃ§Ã£o neste repositÃ³rio.** Os templates servem para entender a arquitetura
(ou para testar em **conta simulada / paper trading**). Se for experimentar, comece por aÃ­.

## Resultado, conforme relatado

| | Valor final |
|---|---|
| Sistema de agentes | ~US$ 9.900 (â‰ˆ âˆ’1,0%) |
| Mesmos US$ 10.000 no S&P 500 | ~US$ 9.980 (â‰ˆ âˆ’0,2%) |
| DiferenÃ§a | o S&P venceu por â‰ˆ 0,8 ponto |

ConclusÃ£o do prÃ³prio autor: 7 pregÃµes Ã© pouco para dizer se a estratÃ©gia funciona.

---

Projeto de estudo do [INEMA.CLUB](https://inema.club) Â· conteÃºdo aberto e gratuito.

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>