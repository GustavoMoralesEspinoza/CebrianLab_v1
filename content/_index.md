---
# Leave the homepage title empty to use the site title
title:
date: 2026-05-20
type: landing

sections:
  - block: hero
    content:
      title: CebrianLab
      image:
        filename: Smart_grids.jpg
      text: |
        <span class="cebrian-hero-tagline">Computational tools for reliable, flexible, and sustainable power distribution networks.</span>

        CebrianLab develops models, algorithms, and decision-support tools for modern power distribution systems, with focus on distributed energy resources, hosting capacity, power quality, reliability, grid flexibility, and smart grid operation.

        <div class="cebrian-actions">
          <a class="btn btn-primary btn-lg" href="/research/">Explore our research</a>
          <a class="btn btn-outline-primary btn-lg" href="/team/">Meet the team</a>
          <a class="btn btn-outline-primary btn-lg" href="/join/">Join us</a>
        </div>
    design:
      background:
        gradient_end: '#f6fbff'
        gradient_start: '#ffffff'

  - block: markdown
    content:
      title: Expertise and Research Activities
      subtitle: Our research combines power system modeling, optimization, simulation, and data-driven methods to support the energy transition in distribution networks.
      text: |
        <div class="cebrian-card-grid cebrian-expertise-grid">
          <article class="cebrian-card">
            <div class="cebrian-icon"><i class="fas fa-bolt"></i></div>
            <h3>Power Distribution Modeling</h3>
            <p>Simulation and analysis of modern distribution networks using computational tools.</p>
          </article>
          <article class="cebrian-card">
            <div class="cebrian-icon"><i class="fas fa-solar-panel"></i></div>
            <h3>Hosting Capacity &amp; DER Integration</h3>
            <p>Assessment of photovoltaic generation, storage systems, electric vehicles, and flexible loads.</p>
          </article>
          <article class="cebrian-card">
            <div class="cebrian-icon"><i class="fas fa-car-battery"></i></div>
            <h3>Energy Storage</h3>
            <p>Modeling, operation, and optimization of battery energy storage systems.</p>
          </article>
          <article class="cebrian-card">
            <div class="cebrian-icon"><i class="fas fa-car-side"></i></div>
            <h3>Electric Mobility</h3>
            <p>Impact assessment and charging strategies for electric vehicles in distribution grids.</p>
          </article>
          <article class="cebrian-card">
            <div class="cebrian-icon"><i class="fas fa-sliders-h"></i></div>
            <h3>Grid Flexibility</h3>
            <p>Flexible operation, control strategies, and active network management.</p>
          </article>
          <article class="cebrian-card">
            <div class="cebrian-icon"><i class="fas fa-lightbulb"></i></div>
            <h3>Demand Response</h3>
            <p>Integration of flexible demand and customer-side resources into grid operation.</p>
          </article>
          <article class="cebrian-card">
            <div class="cebrian-icon"><i class="fas fa-shield-alt"></i></div>
            <h3>Power Quality &amp; Reliability</h3>
            <p>Voltage sags, interruptions, reliability indices, and sensitive customer impacts.</p>
          </article>
          <article class="cebrian-card">
            <div class="cebrian-icon"><i class="fas fa-brain"></i></div>
            <h3>Optimization &amp; AI</h3>
            <p>Genetic algorithms, Monte Carlo simulation, and decision-support methods.</p>
          </article>
          <article class="cebrian-card">
            <div class="cebrian-icon"><i class="fas fa-terminal"></i></div>
            <h3>OpenDSS &amp; Python Tools</h3>
            <p>Development of computational workflows for distribution system simulation.</p>
          </article>
        </div>
    design:
      columns: '1'

  - block: markdown
    content:
      title: Research for the energy transition at the distribution level
      text: |
        <div class="cebrian-statement">
          <p>We are a research group focused on the energy transition at the distribution level. Our work combines power system simulation, optimization algorithms, and data-driven methods to support the integration of renewable energy, storage systems, electric mobility, and flexible demand in modern electrical networks.</p>
        </div>
    design:
      columns: '1'

  - block: markdown
    content:
      title: Principal Investigator
      text: |
        <section class="cebrian-pi-card">
          <div class="cebrian-pi-photo">
            <img src="/author/admin/avatar.png" alt="Juan Carlos Cebrian">
          </div>
          <div class="cebrian-pi-content">
            <p class="cebrian-eyebrow">Professor / Principal Investigator</p>
            <h3>Juan Carlos Cebrian</h3>
            <p class="cebrian-muted">Professor Doctor, Department of Electrical Energy and Automation</p>
            <p class="cebrian-muted">University of Sao Paulo (USP)</p>
            <p>Professor Juan Carlos Cebrian works on power quality, distribution network planning, smart grids, Industry 4.0, Internet of Things, distributed energy resources, and optimization methods applied to modern electric power systems.</p>
            <div class="cebrian-tags">
              <span>Power Quality</span>
              <span>Distribution Planning</span>
              <span>Smart Grids</span>
              <span>Optimization</span>
              <span>DER Integration</span>
            </div>
            <div class="cebrian-link-row">
              <a href="/author/admin/">Profile</a>
              <a href="https://scholar.google.com/citations?user=yBcR3NAAAAAJ&amp;hl=es&amp;oi=ao">Google Scholar</a>
              <a href="https://orcid.org/0000-0001-8507-3791">ORCID</a>
              <a href="https://www.researchgate.net/profile/Juan-Cebrian-6">ResearchGate</a>
              <a href="mailto:juan.cebrian@usp.br">Email</a>
            </div>
          </div>
        </section>
    design:
      columns: '1'

  - block: markdown
    content:
      title: Our Team
      text: |
        CebrianLab brings together faculty, researchers, graduate students, undergraduate students, alumni, and collaborators working on power systems, smart grids, optimization, and renewable energy integration.

        {{< team_summary >}}

        <div class="cebrian-centered-action">
          <a class="btn btn-primary" href="/team/">Meet the full team</a>
        </div>
    design:
      columns: '1'

  - block: markdown
    content:
      title: Featured Projects
      subtitle: Our projects investigate planning, operation, control, and optimization strategies for modern distribution networks under the energy transition.
      text: |
        <div class="cebrian-card-grid cebrian-project-grid">
          <article class="cebrian-card cebrian-project-card">
            <div class="cebrian-badge">Active</div>
            <h3>FlexHostCap - Hosting Capacity in Distribution Networks</h3>
            <p>Development of computational strategies to assess and improve the hosting capacity of distribution networks with high penetration of distributed energy resources.</p>
            <div class="cebrian-tags"><span>Hosting Capacity</span><span>PV</span><span>BESS</span><span>Electric Vehicles</span></div>
            <a class="cebrian-card-link" href="/projects/flexhostcap/">View project</a>
          </article>
          <article class="cebrian-card cebrian-project-card">
            <div class="cebrian-badge">Active / In development</div>
            <h3>Distribution Expansion Planning with Reliability and Power Quality</h3>
            <p>Optimization models for distribution expansion planning considering investment, losses, reliability indices, and power quality impacts.</p>
            <div class="cebrian-tags"><span>Planning</span><span>Reliability</span><span>Power Quality</span><span>Optimization</span></div>
            <a class="cebrian-card-link" href="/projects/distribution-expansion-planning/">View project</a>
          </article>
          <article class="cebrian-card cebrian-project-card">
            <div class="cebrian-badge">In development</div>
            <h3>PV-BESS-EV Integration in Smart Distribution Systems</h3>
            <p>Simulation and optimization of distributed energy resources to support reliable and flexible operation of distribution networks.</p>
            <div class="cebrian-tags"><span>Photovoltaics</span><span>Battery Storage</span><span>EVs</span><span>Smart Grids</span></div>
            <a class="cebrian-card-link" href="/projects/pv-bess-ev-integration/">View project</a>
          </article>
          <article class="cebrian-card cebrian-project-card">
            <div class="cebrian-badge">In development</div>
            <h3>Industry 4.0 Loads and Power Quality Impacts</h3>
            <p>Assessment of power quality disturbances and their impact on sensitive industrial customers and modern production systems.</p>
            <div class="cebrian-tags"><span>Sensitive Loads</span><span>Voltage Sags</span><span>Interruptions</span><span>Financial Impacts</span></div>
            <a class="cebrian-card-link" href="/projects/power-quality-industry-4-0/">View project</a>
          </article>
        </div>
    design:
      columns: '1'

  - block: markdown
    content:
      title: Selected Publications
      subtitle: Recent and selected research outputs from CebrianLab.
      text: |
        {{< selected_publications >}}

        <div class="cebrian-centered-action">
          <a class="btn btn-primary" href="/publications/">View all publications</a>
        </div>
    design:
      columns: '1'

  - block: markdown
    content:
      title: Where to meet us
      text: |
        Follow our participation in conferences, workshops, seminars, and research events.

        <div class="cebrian-card-grid cebrian-news-grid">
          <article class="cebrian-card">
            <p class="cebrian-eyebrow">Date to be announced</p>
            <h3>Upcoming conference presentation</h3>
            <p>Details will be updated soon.</p>
          </article>
          <article class="cebrian-card">
            <p class="cebrian-eyebrow">Date to be announced</p>
            <h3>Workshop or seminar activity</h3>
            <p>Details will be updated soon.</p>
          </article>
          <article class="cebrian-card">
            <p class="cebrian-eyebrow">Date to be announced</p>
            <h3>Project milestone</h3>
            <p>Details will be updated soon.</p>
          </article>
        </div>

        <div class="cebrian-centered-action">
          <a class="btn btn-primary" href="/news/">See all news and events</a>
        </div>
    design:
      columns: '1'

  - block: markdown
    content:
      title: Collaborations & Partners
      text: |
        We collaborate with academic institutions, research centers, and partners interested in smart grids, distribution systems, and the energy transition.

        <div class="cebrian-partner-grid">
          <div class="cebrian-partner-placeholder">Partner logo</div>
          <div class="cebrian-partner-placeholder">Research center</div>
          <div class="cebrian-partner-placeholder">Institution</div>
        </div>
    design:
      columns: '1'

  - block: markdown
    content:
      title: Join CebrianLab
      text: |
        We welcome motivated undergraduate, MSc and PhD students, postdoctoral researchers, and external collaborators interested in smart grids, power distribution systems, optimization, simulation, and the energy transition.

        <div class="cebrian-card-grid cebrian-join-grid">
          <article class="cebrian-card">
            <h3>Undergraduate Students</h3>
            <p>Work on simulations, data analysis, OpenDSS, Python, and visualization tools.</p>
          </article>
          <article class="cebrian-card">
            <h3>MSc and PhD Students</h3>
            <p>Develop research on hosting capacity, DER integration, optimization, reliability, and smart grid operation.</p>
          </article>
          <article class="cebrian-card">
            <h3>Postdoctoral Researchers</h3>
            <p>Contribute to advanced research on modern distribution systems and computational tools.</p>
          </article>
          <article class="cebrian-card">
            <h3>External Collaborators</h3>
            <p>Collaborate on academic and applied research in power systems and energy transition.</p>
          </article>
        </div>

        <div class="cebrian-actions cebrian-actions-center">
          <a class="btn btn-primary btn-lg" href="/join/">Open opportunities</a>
          <a class="btn btn-outline-primary btn-lg" href="/contact/">Contact us</a>
        </div>
    design:
      columns: '1'
      background:
        color: '#f4f8fb'
---
