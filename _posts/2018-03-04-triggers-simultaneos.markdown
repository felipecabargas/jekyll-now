---

layout: post
author: "A. Cabargas"
categories: rules
tags: [stack]
image: stack.jpg
title:  "#1 | Triggers simultáneos"
---
Que pasa cuando varios triggers se activan en la misma fase? O ante el mismo evento? Que pasa si esos triggers pertenecen al mismo jugador? Que pasa si son de diferentes jugadores? Eso es lo que intentare explicar hoy en la primera edición de "Jueceando"

## Pertenecientes al mismo jugador

Supongamos que tenemos [Zendikar Resurgent](http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=433092) y [Hazoret's Monument](http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=426931) en juego, y casteamos [Goblin Trailblazer]()

| Stack | En Juego |
|:--|:--|
| ![]({{"assets/img/goblin-trailblazer.png" | absolute_url}}) | ![]({{"assets/img/zendikar-resurgent.png" | absolute_url}}) ![]({{"assets/img/hazoreths-monument.png" | absolute_url}}) |

Qué sucede primero? Descartamos y robamos por `Hazoret's Monument` o robamos por `Zendikar Resurgent`?

Cuando 2 o más triggers suceden simultáneamente, y todos pertenecen al mismo jugador, el jugador puede ponerlos en la pila en el orden que desee, y estos se resolverán en orden inverso de como fueron puestos en el stack, así:

Si ponemos el trigger de `Zendikar Resurgent` y luego el de `Hazoret's Monument` encima en el stack, asi:

| Stack | |
|:--|:--|
| ![]({{"assets/img/hm-trigger.png" | absolute_url}}) | `Hazoret's Monument` Trigger|
| ![]({{"assets/img/zr-trigger.png" | absolute_url}}) | `Zendikar Resurgent` Trigger|

1. Se resuelve el trigger de `Hazoret's Monument`: Descartamos una carta y robamos una.
2. Se resuelve el trigger de `Zendikar Resurgent`: Robamos una carta

## Pertenecientes a jugadores distintos

Supongamos un juego 1v1, el Jugador 1 esta iniciando su `upkeep` (mantenimiento) y tiene en juego un [Shivan Dragon](http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=429911) y un [Wolfcaller's Howl](http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=430388), mientras que su oponente (Jugador 2) controla a [Sheoldred, Whispering One](http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=438674). Que sucede? Obtiene el token de criatura `Wolf 2/2` primero para sacrificarlo o esta obligado a sacrificar `Shivan Dragon` ?

### Jugador 1

| Jugador 1 |
|:--|
| ![]({{"assets/img/shivan-dragon.png" | absolute_url}}) ![]({{"assets/img/wolfcaller-howl.png" | absolute_url}}) |

### Jugador 2

| Jugador 2 |
|:--|
| ![]({{"assets/img/sheoldred.png" | absolute_url}}) |

Este caso es considerado por las reglas en la seccion **603 (Triggered Abilities)** y la seccion **116 (Timing and Priority)** de las Reglas.

> **603.3.** Once an ability has triggered, its controller puts it on the stack as an object that’s not a card the
next time a player would receive priority. See rule 116, “Timing and Priority.” The ability becomes
the topmost object on the stack. It has the text of the ability that created it, and no other
characteristics. It remains on the stack until it’s countered, it resolves, a rule causes it to be removed
from the stack, or an effect moves it elsewhere.

> **116.5.** Each time a player would get priority, the game first performs all applicable state-based actions
as a single event (see rule 704, “State-Based Actions”), then repeats this process until no state-based
actions are performed. Then triggered abilities are put on the stack (see rule 603, “Handling
Triggered Abilities”). These steps repeat in order until no further state-based actions are performed
and no abilities trigger. Then the player who would have received priority does so.

En este caso, lamentablemente, el Jugador 1 esta obligado a sacrificar su `Shivan Dragon`. Esto se debe a que según las reglas, el jugador activo (el jugador cuyo turno esta iniciando)  pone sus triggers en el stack primero, pasando prioridad a los jugadores no activos que solo entonces pueden poner sus trigger en el stack. En nuestro caso, el stack queda así:

| Stack | |
|:--|:--|
| ![]({{"assets/img/s-trigger.png" | absolute_url}}) | `Sheoldred, Whispering One` Trigger|
| ![]({{"assets/img/wch-trigger.png" | absolute_url}}) | `Wolfcaller's Howl` Trigger|

1. Se resuelve el trigger de `Sheoldred, Whispering One`: Jugador 1 sacrifica una criatura (en este caso `Shivan Dragon`)
2. Se resuelve el trigger de `Wolfcaller's Howl`: El Jugador 1 crea un token de criatura `Wolf 2/2`
