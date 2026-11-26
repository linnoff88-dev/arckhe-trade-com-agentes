ï»¿# Trade com Agentes ê¢â¬â o mêÂ©todo do desafio de 7 dias

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="48" />
  <p><strong>Arckhé AI</strong></p>
</div>


**ê°Å¸â¡Â§ê°Å¸â¡Â· [PortuguêÂªs](README.md) êÂ· ê°Å¸â¡Âºê°Å¸â¡Â¸ [English](README.en.md) êÂ· ê°Å¸â¡Âªê°Å¸â¡Â¸ [EspaêÂ±ol](README.es.md)**

[![Trade com Agentes](guia/assets/banner.jpg)](https://inematds.github.io/trade-com-agentes/guia/)

> ## ê¢Å¡Â ê¯Â¸Â Leia antes: isto êÂ© um texto de estudo, nêÂ£o uma recomendaêÂ§êÂ£o
>
> **Eu nêÂ£o confio nisso para operar.** Trade êÂ© risco alto, tem variêÂ¡veis demais e **sempre tem
> alguêÂ©m do outro lado com informaêÂ§êÂ£o que a gente nêÂ£o tem**. Este repositêÂ³rio nêÂ£o êÂ© conselho
> financeiro, nêÂ£o êÂ© estratêÂ©gia validada e nêÂ£o êÂ© convite para colocar dinheiro em robêÂ´.
>
> O objetivo êÂ© outro: **aprender com o que ele fez** ê¢â¬â como montou os agentes, como passou o
> contexto de um para o outro, onde travou e o que mudou no caminho. O prêÂ³prio resultado do
> desafio mostra o ponto: em 7 dias, o sistema **perdeu para o S&P 500**.

## ê°Å¸ââ Guia de uso

Guia completo (landing + passo a passo): **https://inematds.github.io/trade-com-agentes/guia/**

## De onde vem

VêÂ­deo no YouTube: **"I Gave GPT 6 Astra $10,000 to Trade Stocks...And This Happened"** ê¢â¬â
<https://www.youtube.com/watch?v=eg_1NXDcoPk>

O autor deu US$ 10.000 de dinheiro de verdade para um agente no **Codex com GPT-6 Astra
(esforêÂ§o alto)** operar aêÂ§êÂµes por **7 pregêÂµes**, com a meta de **bater o S&P 500**. Diferente de
um teste anterior dele (com OpenClaw, 30 dias, sem mexer), aqui ele podia fazer **atêÂ© duas
mudanêÂ§as por dia** ê¢â¬â mas nêÂ£o podia desligar o sistema, mesmo perdendo.

Tudo que estêÂ¡ aqui êÂ© **parêÂ¡frase do vêÂ­deo**. NêÂºmeros sêÂ£o **"conforme relatado no vêÂ­deo"**; nada
foi auditado. A transcriêÂ§êÂ£o êÂ© automêÂ¡tica, entêÂ£o alguns nomes podem estar ouvidos errado (ver
[metodo/06-diario-7-dias.md](metodo/06-diario-7-dias.md)).

## O mêÂ©todo em uma tela

```
07:45  prêÂ©-mercado   ê¢â â lêÂª notêÂ­cias, confere conta, escolhe o que vigiar
09:30  1h de pregêÂ£o  ê¢â â procura a primeira entrada que passe nos filtros
11:00  meio do dia   ê¢â â revisa posiêÂ§êÂµes, êÂºltima chance de nova entrada
13:00  tarde         ê¢â â administra o que estêÂ¡ aberto
14:15  fechamento    ê¢â â encerra as posiêÂ§êÂµes restantes
14:45  confirmaêÂ§êÂ£o   ê¢â â confere se zerou e registra o resultado do dia
15:15  aviso final   ê¢â â notificaêÂ§êÂ£o
(horêÂ¡rio Central dos EUA ê¢â¬â pregêÂ£o das 8:30 êÂ s 15:00 CT)

Cada rotina acorda ê¢â â LêÅ  o bilhete de handoff da anterior ê¢â â age ê¢â â ESCREVE o prêÂ³ximo bilhete.
Todas rodam na MESMA thread: parece um agente sêÂ³ trabalhando o dia inteiro.
```

A partir do dia 2 entrou uma segunda peêÂ§a: o modelo **se recusou a executar ordens sozinho**.
SoluêÂ§êÂ£o dele: o Astra vira sêÂ³ o **estrategista** e termina cada rotina mandando um **e-mail** com as
recomendaêÂ§êÂµes para um **bot executor** (que tem e-mail prêÂ³prio + webhook). O bot acorda com o
e-mail e manda a ordem para a corretora **Alpaca**.

## ConteêÂºdo

| Arquivo | O que tem |
|---|---|
| [metodo/01-visao-geral.md](metodo/01-visao-geral.md) | Regras do desafio, peêÂ§as e arquitetura |
| [metodo/02-rotinas.md](metodo/02-rotinas.md) | As 7 rotinas do dia, uma a uma |
| [metodo/03-handoff.md](metodo/03-handoff.md) | A continuidade: bilhete de passagem entre agentes |
| [metodo/04-estrategista-executor.md](metodo/04-estrategista-executor.md) | Por que separou quem pensa de quem executa |
| [metodo/05-portoes-de-risco.md](metodo/05-portoes-de-risco.md) | Filtros, relaêÂ§êÂ£o risco/retorno e como foram afrouxados |
| [metodo/06-diario-7-dias.md](metodo/06-diario-7-dias.md) | O que aconteceu em cada dia (nêÂºmeros relatados) |
| [metodo/07-licoes.md](metodo/07-licoes.md) | O que dêÂ¡ para aprender ê¢â¬â e por que eu nêÂ£o copiaria |
| [templates/rotinas.yaml](templates/rotinas.yaml) | Agenda das rotinas em formato de configuraêÂ§êÂ£o |
| [templates/handoff.md](templates/handoff.md) | Modelo do bilhete de handoff |
| [templates/prompt-rotina.md](templates/prompt-rotina.md) | Modelo de prompt de cada rotina |
| [templates/recomendacao.json](templates/recomendacao.json) | Formato do e-mail estrategista ê¢â â executor |

**NêÂ£o hêÂ¡ cêÂ³digo de operaêÂ§êÂ£o neste repositêÂ³rio.** Os templates servem para entender a arquitetura
(ou para testar em **conta simulada / paper trading**). Se for experimentar, comece por aêÂ­.

## Resultado, conforme relatado

| | Valor final |
|---|---|
| Sistema de agentes | ~US$ 9.900 (ê¢â°Ë ê¢Ëâ1,0%) |
| Mesmos US$ 10.000 no S&P 500 | ~US$ 9.980 (ê¢â°Ë ê¢Ëâ0,2%) |
| DiferenêÂ§a | o S&P venceu por ê¢â°Ë 0,8 ponto |

ConclusêÂ£o do prêÂ³prio autor: 7 pregêÂµes êÂ© pouco para dizer se a estratêÂ©gia funciona.

---

Projeto de estudo do [INEMA.CLUB](https://inema.club) êÂ· conteêÂºdo aberto e gratuito.

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>