---
title: "Reconfiguration of distribution networks to minimize loss and disruption costs using genetic algorithms"
date: 2010-01-01
publishDate: 2009-09-19T00:00:00Z

# Publication type: journal-article, paper-conference, etc.
publication_types: ['journal-article']

# Journal / venue
publication: "Electric Power Systems Research"
publication_short: "EPSR"
volume: "80"
pages: "53–62"
publisher: "Elsevier"

# Authors (usa nombres directos o slugs de tus páginas de 'people' si ya existen)
authors:
  - Juan Carlos Cebrian Amasifen
  - Nelson Kagan

# DOI y enlaces
doi: "10.1016/j.epsr.2009.08.005"
url_pdf: "files/cebian-2010-epsr.pdf"       # coloca el PDF aquí (static/files/…)
url_code: ""
url_dataset: ""
url_project: ""
url_slides: ""
url_video: ""
# url_source: ""                           # si quieres añadir el enlace de ScienceDirect

# Palabras clave / etiquetas
tags:
  - Distribution Network Reconfiguration
  - Power Quality
  - Voltage Sags
  - Genetic Algorithms
  - Monte Carlo

# Resumen corto que aparece en tarjetas/listas
summary: "Proposes an evolutionary algorithm for radial distribution network reconfiguration that jointly minimizes technical losses and costs due to long interruptions and voltage-sag-induced process disruptions, integrating Monte Carlo–based power quality assessment into the optimization."

# Abstract (paráfrasis del paper)
abstract: >
  This work presents an evolutionary algorithm (EA) for the reconfiguration of radial distribution systems that optimizes a composite objective: network energy losses and customer costs from power quality events, namely long-duration interruptions and process disruptions caused by voltage sags. The formulation includes load-flow based penalties for voltage and branch loading limits, while a Monte Carlo simulation estimates interruption and sag frequency and associated costs. The EA employs a decimal codification of interconnection branches, elitist/tournament selection, a topology-aware recombination that preserves radiality, and a mutation operator designed to avoid islanding. Tests on 14- and 135-bus systems show that enforcing population diversity and dynamically tuning recombination/mutation rates improves convergence, yielding configurations with reduced losses and lower total costs compared with prior methods. :contentReference[oaicite:0]{index=0}

# Destacar en portada
featured: true

# Imagen (opcional)
image:
  caption: "Distribution network reconfiguration with EA."
  focal_point: "Center"

# Bibliographic data extra (opcional)
projects: []
# language: en
# reading_time: true
# profile: false
---
