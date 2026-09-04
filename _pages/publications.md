---
layout: page
permalink: /publications/
title: PAPERS
description: This page contains published papers and papers under review.
nav: false
nav_order: 2
---

<!-- _pages/publications.md -->

<!-- Bibsearch Feature -->

{% include bib_search.liquid %}

<div class="publications">

<h2>Published</h2>

{% bibliography --group_by none --query @article %}

<h2>Under Review</h2>

{% bibliography --group_by none --query @unpublished %}

</div>
