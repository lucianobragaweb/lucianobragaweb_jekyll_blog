---
layout: post
title:  Comandos Úteis no Docker
date:   2020-01-07 14:00:00
categories: DevOps
author: lucianobragaweb
tags: [Docker]
---

Apesar de ter resistido um pouco antes de entrar nessa onda de *Docker* hoje vejo o quanto esta ferramenta é útil. E como é humanamente impossível ter todos os comandos e códigos decorados vou listar aqui alguns que costumos usar. Pode ser que essa lista seja expandida, e caso queira incluir algum comando basta mandar um **Pull Request**, afinal estes são os que uso com mais frequência e precisam estar ali sempre a mão.


> “Fique a vontade para incluir comandos úteis a esta lista!”.

### Listar Containers em Execução

`docker ps`

### Apagar todas as imagens

`docker rm $(docker ps -a -q) -f`