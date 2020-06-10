---
title: "Scala: sua próxima linguagem?"
date: "2009-08-10"
author: "rafael.ferreira"
authorEmail: "rafael.ferreira@caelum.com.br"
main_guide: "main_guide"
main_category: "geral"
---

Uma das mudanças mais pronunciadas no cenário da informática é a modificação no  perfil da [lei de Moore](http://en.wikipedia.org/wiki/Moore%27s_law). Gordon Moore, fundador da Intel, observou que o número de transistores em um microprocessador dobra a cada dois anos. Esse crescimento exponencial, até poucos anos atrás, era refletido em um aumento do clock – a velocidade – dos processadores. Mas agora [o clock atingiu um limite](http://www.gotw.ca/publications/concurrency-ddj.htm "The Free Lunch is Over - Herb Sutter"), e o adicional de transistores é cada vez mais direcionado para aumentar o número de _cores_ de processadores e, assim, ampliar o nível de concorrência.

O que isso tudo significa é que nós, programadores comums, não podemos mais nos dar ao luxo de ignorar as dificuldades da programação concorrente. E essas dificuldades não são pequenas, como qualquer um que já teve de programar bastante para concorrência em Java, usando as primitivas `wait-notify` de um monitor, deve saber. O pior: você pode errar quando definir suas regiões críticas, e isso só será descoberto quando um entrelaçamento de threads específico ocorrer, o que pode vir a demorar dias com o sistema em produção, para só então o bug aparecer.

No fundo, os problemas da programação concorrente têm origem na dificuldade em sincronizar mudanças de estado. Mas existe um estilo de programação que procura evitar ao máximo mudanças explícitas de estado: a [programação funcional](http://www.cs.chalmers.se/~rjmh/Papers/whyfp.html "Why Functional Programming Matters - John Hughes"), que [tem ganhado muita atenção para desenvolver sistemas web](http://steve.vinoski.net/pdf/IC-Welcome_to_the_Functional_Web.pdf). [Scala](http://www.scala-lang.org/) é uma linguagem de programação moderna – sua primeira versão é de 2003 – e procura vencer as batalhas da concorrência num campo familiar: a JVM. Comprometida com o pragmatismo, Scala não é uma linguagem funcional pura, mas híbrida, procurando unir o que há de mais avançando em orientação a objetos com conceitos funcionais. Foi criada pelo professor [Martin Odersky](http://lampwww.epfl.ch/~odersky/), que tem a distinção de ser o autor do compilador de Java do JDK, e vem sendo desenvolvida pela [sua equipe](http://lampwww.epfl.ch/ "LAMP - Programming Methods Laboratory") na [universidade suíça EPFL](http://www.epfl.ch/).

Embora [facilitar a programação concorrente](http://scala-blogs.org/2008/09/scalable-language-and-scalable.html "Um exemplo simples de codigo paralelo em Scala vs em Java") seja [uma meta declarada](http://www.scala-lang.org/sites/default/files/odersky/scalaliftoff2009.pdf) através de imutabilidade e outros recursos, existem motivos para se interessar por Scala mesmo para quem não pretende se aventurar além do código sequencial: [Inferência de Tipos](http://www.scala-lang.org/node/127) permite que se programe de maneira menos burocrática sem perder as garantias de correção, refactoring e auto complete, a que estamos acostumados quando desenvolvemos em Java, [Funções Anônimas](http://www.scala-lang.org/node/133 "A mesma coisa que andam chamando de closures nas discussões sobre Java 7 e 8.") permitem um estilo de programação altamente produtivo, especialmente ao lidar com [coleções](http://www.ibm.com/developerworks/java/library/j-scala06278.html), [Pattern Matching](http://www.scala-lang.org/node/120) ajuda a trabalhar com estruturas aninhadas, como ao fazer [parsing de XML](http://scala.sygneca.com/code/xml-pattern-matching), e a sintaxe flexível é ótima para [DSLs internas](http://www.scala-lang.org/node/1403 "Exemplo de uma Domain Specific Language em Scala"). Esses e outros motivos levaram o [Twitter a migrar de Ruby para Scala](http://www.artima.com/scalazine/articles/twitter_on_scala.html) alguns de seus subsistemas.

Código Scala compila para bytecodes java normais, e é trivial invocar código Java de Scala e vice-versa. Tamanha integração com o ambiente Java levou o criador de Groovy, James Strachan, a [especular que Scala é o melhor candidato a substituir Java no longo prazo](http://macstrac.blogspot.com/2009/04/scala-as-long-term-replacement-for.html "Scala as long term replacement for Javac - James Strachan blog post"). Não contente com esta polêmica, Strachan ainda afirma que se conhecesse Scala na época, não teria enxergado a necessidade da criação do Groovy. O próprio [James Gosling afirmou que escolheria por Scala se tivesse de optar por outra linguagem](http://www.adam-bien.com/roller/abien/entry/java_net_javaone_which_programming).

[Não é de hoje](https://blog.caelum.com.br/2009/06/25/a-jvm-e-as-outras-linguagens-voce-esta-preparado/) que a Caelum acredita em um futuro plural, e no melhor estilo _programação poliglota_, já desenvolvemos partes importantes de um sistema Java em Scala, onde consideramos que ela era cabível. Para quem quiser saber mais sobre Scala, [o tour da linguagem](http://www.scala-lang.org/node/104) é um bom recurso para matar a curiosidade. Mas é claro que o melhor meio de conhecer uma linguagem é meter a mão na massa, e para isso recomendo o tutorial [First Steps to Scala](http://www.artima.com/scalazine/articles/steps.html), de autoria do próprio Martin Odersky colaborando com Bill Venners e Lex Spoon. Esse tutorial foi extraído de trechos do livro [Programming in Scala](http://www.artima.com/shop/programming_in_scala), dos mesmos autores.

Três últimas recomendações, agora mais sobre programação concorrente em geral: veja [os slides de uma apresentação do Jonas Bonér sobre os diversos paradigmas de programação concorrente e paralela](http://jonasboner.com/talks/state_youre_doing_it_wrong/html/all.html), [o vídeo](http://www.infoq.com/presentations/fortress-steele) de uma apresentação do [Guy Steele](http://en.wikipedia.org/wiki/Guy_Steele), um dos "criadores" do Java, sobre Fortress, sua linguagem de pesquisa para computação científica maciçamente paralela, e um [capítulo de livro](http://www.info.ucl.ac.be/~pvr/VanRoyChapter.pdf "PDF: Programming Paradigms for Dummies: What Every Programmer Should Know") do Peter van Roy, também sobre paradigmas de programação concorrente e paralela. Pra quem prefere o bom e velho Java, vale o livro [Java Concurrency in Practice](http://www.amazon.com/Java-Concurrency-Practice-Brian-Goetz/dp/0321349601), que trata o assunto a fundo e chega a detalhes da JVM e do funcionamento do pacote `java.util.concurrent`.