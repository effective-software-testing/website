---
title: "Using the book in classroom"
layout: post
permalink: /for-teachers
hide_newsletter: true
---

Are you interested in using this book in your classroom? Universities are more and more focusing on software testing. Unfortunately, most books out there are either too theoretical or too practical. _Effective Software Testing: A Developer's Guide_ gives students a pragmatic and solid view on modern software testing practices. 

## How I've been using it

I've been using my own book to teach software testing at the Delft University of Technology. 

The course is stuctured as follows:

* I follow the flipped classroom model, where students read the chapters before the lecture. In the lecture, I then engage students through debates, discussions, live coding, and exercises. You can read [my blog post about flipped classroom](https://www.mauricioaniche.com/blog/what-did-i-learn-from-flipping-my-classroom/). All [my support slides](https://drive.google.com/drive/folders/1rFcF4Ia32q-8NOKIcBm3xzVE2tMm8U_J?usp=drive_link) are available in Google Docs, feel free to use them as inspiration.

* In the lab, students solve multiple exercises, each focusing on a technique discussed in the book: specification-based and structural testing, mocking, property-based testing, web testing, and SQL testing. We use our in-house tool called [Andy](https://github.com/SERG-Delft/andy) to give students automated feedback. You can use the tool or just the exercises. Everything, including solutions, are in the repository. 

* Students go through a midterm and a final exam. Both of them have a similar structure. They are mostly coding exams where I give students questions similar to the ones they've seen during the practice. I often complement the coding questions with multiple choice questions to also capture their theoretical knowledge.

In terms of schedule, my course has nine weeks and around 14 lectures of 1.5 hours during these weeks. I try to never let them have to read more than 2 chapters per week, otherwise it's too intense for them. I go through the chapters in the order of the book. 

Although it's mostly one chapter per lecture, sometimes I combine two chapters in one lecture. For example, I have been able to talk about design by contracts and property-based testing in a single lecture. Test code smells and web testing also often fits in one lecture.

As a complement, I invite guests to talk about their experiences with testing in between the lectures. Guest lectures are highly appreciated by the students. I often have 3-4 guests per edition of the course.

I hope this inspires you in creating your own testing course. Feel free to drop me an e-mail in case of more questions!


## Who's using it?

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
* Colgate University, USA ([Dr. Georgiana Haldeman](https://www.colgate.edu/about/directory/ghaldeman))
* King Saud University, Saudi Arabia (Dr. Abdulaziz Alshayban)

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
      ['Switzerland', 100],
      ['Saudi Arabia', 100]
    ]);

    var options = {};

    var chart = new google.visualization.GeoChart(document.getElementById('regions_div'));

    chart.draw(data, options);
  }
</script>