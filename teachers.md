---
title: "Using the book in classroom"
layout: post
permalink: /for-teachers
hide_newsletter: true
---

Are you interested in using this book in your classroom? Universities are more and more focusing on software testing. Unfortunately, most books out there are either too theoretical or too practical. The _Effective Software Testing: A Developer's Guide_ book gives students a pragmatic and solid view on modern software testing practices. 

I have been using my own book to teach software testing at Delft University of Technology. I can help you in understanding how to adopt this book. Send me an e-mail and we schedule a conversation about it. 

We will discuss:

* How to flip the classroom using my book as the main source of study
* How to make use of our 50+ coding exercises together with our open-source grading tool
* How to engage students with pragmatic discussions and live coding
* How to obtain a nice discount for your students to buy the book

This book is currently being used by: 

* Delft University of Technology, Netherlands ([Dr. Maurício Aniche](https://www.mauricioaniche.com)), the author of the book
* University of Zürich, Switzerland ([Prof. Dr. Alberto Bacchelli](https://sback.it))
* Pontifícia Universidade Católica - Rio Grande do Sul, Brazil ([Prof. Dr. Bernardo Copstein](https://www.linkedin.com/in/bernardo-copstein-3226095))
* Universidade de Passo Fundo, Brazil ([Prof. Dr. Alexandre Lazaretti Zanatta](https://www.linkedin.com/in/alexandre-lazaretti-zanatta-b7a461115/))
* Università degli Studi di Bari, Italy ([Dr. Azzurra Ragone](https://www.linkedin.com/in/azzurraragone/))
* University of Victoria, Canada ([Prof Dr. Margaret-Anne Storey](https://www.margaretstorey.com/))
* Carnegie Mellon University, USA ([Dr. Michael Hilton](https://www.cs.cmu.edu/~mhilton/))
* University of São Paulo, Brazil ([Prof. Dr. Alfredo Goldman](https://www.ime.usp.br/~gold/new/))
* University of Tirana, Albania ([Dr. Klesti Hoxha](https://klestihoxha.al))
* Radboud University, the Netherlands ([Dr. Bin Lin](https://binlin.info/))
* University of Tübingen, Germany ([Dr. Jonathan Brachthäuser](https://se.cs.uni-tuebingen.de/group/))
* École de Technologie Supérieure (l'ÉTS), Canada ([Dr. Fabio Petrillo](https://www.etsmtl.ca/en/research/professors/fpetrillo/))
* State University of Feira de Santana, Brazil ([Dr. Larissa Rocha](https://pgcc.uefs.br/sobre/docentes/larissa))

<div id="regions_div" style="width: 900px; height: 500px;"></div>

If you are using this book, let me know, and I'll add you here!

<script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>

<script type="text/javascript">
  google.charts.load('current', {
    'packages':['geochart'],
  });
  google.charts.setOnLoadCallback(drawRegionsMap);

  function drawRegionsMap() {
    var data = google.visualization.arrayToDataTable([
      ['Country', 'Popularity'],
      ['Netherlands', 100],
      ['Brazil', 100],
      ['Italy', 100],
      ['Canada', 100],
      ['United States', 100],
      ['Albania', 100],
      ['Germany', 100],
      ['Switzerland', 100]
    ]);

    var options = {};

    var chart = new google.visualization.GeoChart(document.getElementById('regions_div'));

    chart.draw(data, options);
  }
</script>