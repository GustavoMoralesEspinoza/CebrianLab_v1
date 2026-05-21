---
title: Research
date: 2026-05-21
type: landing

sections:
  - block: markdown
    content:
      title: Research
      subtitle: Research areas and projects focused on modern power distribution systems, DER integration, power quality, reliability, resilience, optimization, and digital distribution technologies.
      text: |
        <section class="cebrian-research-hero">
          <div class="cebrian-research-hero-copy">
            <p>CebrianLab develops computational models, optimization algorithms, and decision-support tools for the planning, operation, control, and digitalization of modern distribution networks. Our research connects power system simulation, distributed energy resources, power quality, reliability, grid flexibility, and artificial intelligence.</p>
            <div class="cebrian-actions">
              <a class="btn btn-primary" href="#research-projects">View projects</a>
              <a class="btn btn-outline-primary" href="../publications/">View publications</a>
            </div>
          </div>
          <div class="cebrian-research-hero-image">
            <picture>
              <source srcset="{{< relurl "images/webp/hero-flexible-grids.webp" >}}" type="image/webp">
              <img src="{{< relurl "images/hero/hero-flexible-grids.png" >}}" alt="Flexible distribution grids with optimization and distributed energy resources">
            </picture>
          </div>
        </section>
    design:
      columns: '1'

  - block: markdown
    content:
      title: Research Focus Areas
      text: |
        {{< research_focus_grid >}}
    design:
      columns: '1'
      background:
        color: '#f6fbff'

  - block: markdown
    content:
      title: Research Projects
      text: |
        <p id="research-projects" class="cebrian-section-intro">Our projects combine simulation, optimization, data-driven methods, and power system analysis to address the challenges of distribution networks under the energy transition.</p>

        {{< research_projects_grid >}}
    design:
      columns: '1'

  - block: markdown
    content:
      title:
      text: |
        <section class="cebrian-research-cta">
          <h2>Interested in collaborating or developing a student project with CebrianLab?</h2>
          <div class="cebrian-actions cebrian-actions-center">
            <a class="btn btn-primary btn-lg" href="../join/">Join us</a>
            <a class="btn btn-outline-primary btn-lg" href="../contact/">Contact us</a>
            <a class="btn btn-outline-primary btn-lg" href="../publications/">View publications</a>
            <a class="btn btn-outline-primary btn-lg" href="../impact/">Explore impact</a>
          </div>
        </section>
    design:
      columns: '1'
      background:
        color: '#f4f8fb'
---
