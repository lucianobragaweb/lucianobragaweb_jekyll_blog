---
layout: post
title:  Curtir no Facebook automaticamente
date:   2017-06-25 10:00:00
categories: Others
author: lucianobragaweb
tags: [Facebook]
---

É cada ideia que surge quando estamos com a mente ociosa que acabamos fazendo dessas coisas. Pois bem, vou explicar o que se passa.

Estava eu ali rolando a Timeline do Facebook quando pensei…

> “E se eu pudesse curtir todos os posts e comentários sem precisar fazer nada, no piloto automático”.

Nem eu mesmo sei por que me ocorreu este pensamento, mas programador é o ser mais preguiçoso que pode existir. E é por isso que sempre estamos desenvolvendo soluções para automatizar tarefas. Talvez para mim isso não tenha uma utilidade pratica, mas pode ter para você que chegou até este artigo buscando no Google.

## Como isso é possível??
Dei um inspect no console do Google Chrome e logo descobri que no link do botão Curtir do Facebook havia uma class chamada UFILikeLink. A partir dai comecei a criar um script para pesquisar dentro da página todos os links com esta class e realizar a ação de click, simulando uma ação do usuário.

Essa ação é realizada em um intervalo de tempo definido randomicamente, visando evitar alguma detecção de padrão pelo algoritmo do Facebook e eventual bloqueio da conta. Nos testes que fiz não houve bloqueio em nenhum momento.

O resultado foi este código que aparece abaixo.

```js
var HTMLTagA= document.getElementsByTagName("a");
var cnt=0;
var i=0;

var randon = 150; // Internavo Inicial
var TimerFunCall = setInterval(Timer, randon);
 
function Timer() {
	if (i<HTMLTagA.length){
		if(HTMLTagA[i].outerHTML.contains('UFILikeLink')){
			cnt = cnt + 1;
			var randon = Math.floor(Math.random() * 503) + 152 ; // Intervalo randomico
			console.log ("Clicou em Curtir: " + cnt + " Intervalo: " + randon); // Mostra mensagem no console
			HTMLTagA[i].click();
		}
	} else {
    		console.log('Total de Links Processados: ' + HTMLTagA.length);
		clearInterval(TimerFunCall);
	}
	i=i+1;
	return i;
}
```

## Como faço para curtir automaticamente no Facebook
Para que este código funcione, primeiro você precisa se conectar à sua Conta do Facebook e depois seguir os passos seguintes.

1. Para escrever o código, abra a janela do console do seu navegador. Use estas teclas para o navegador correspondente: Firefox (F12), Chrome (F12)

2. O navegador abrirá uma janela na parte inferior da página com guias — “Inspector”, “Console”, “Depurador”, “Editor de estilos”, etc.,
Escolha a guia “Console”.

3. Copie o código, cole na janela do console e pressione “Enter”.

## Curtir automaticamente pode não ser uma boa ideia

Uma situação chata que não tem como evitar é que você vai curtir inclusive conteúdo adulto ou assuntos que não são do seu interesse. Então antes de sair curtindo tudo por ai lembre que fizemos aqui apenas uma experiência para demostrar a aplicação de um script que manipula a Timeline.

> Importante: Antes de mais nada quero deixar claro que isso foi apenas uma experiência e em nenhum momento estou incentivando a utilização deste script afim de manipular o Facebook. Apenas disseminando conhecimento.

## Potencial disso em uma aplicação maliciosa
Na verdade, o que fiz com esse script é algo muito simples. Para quem conhece a linguagem JavaScript não tem segredo nisso. Eu pensei que o Facebook tivesse algum mecanismo para prevenir ações como esta, pelo visto não tem.

Pra mim a utilidade foi aprendizado. Mas imagina isso em uma extensão maliciosa que se instale no Chrome ou Mozila, fazendo interação automática em sua Timeline??

E você?? Concorda que está é uma vulnerabilidade que possa ser explorada através de extensões no navegador ou algo do gênero??