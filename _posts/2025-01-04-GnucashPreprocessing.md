---
layout: post
title: Gnucash Processing
date: '2025-01-04T10:10:00.000+05:30'
author: Abhijit
tags: foss, hacking
categories: Software
modified_time: '2025-01-04T10:10:00.000+05:30'
---

I have been using gnucash for a while now for tracking transactions,
but the outputs of most banks do not have the date or amounts in a format that
gnuacash accepts. For example, Gnucash requires the date in y-m-d (with hyphens)
and numerals with no comma separators. Hence, some simple python pre-processing
is necessary. In early 2024 I wrote scripts to do this pre-preprocessing for SBI and Canara Bank which I am publishing on Github.