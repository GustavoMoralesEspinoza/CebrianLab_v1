---
title: News & Events
date: 2026-05-20
type: landing

sections:
  - block: markdown
    content:
      title: News & Events
      text: |
        Updates about publications, conferences, workshops, seminars, project milestones, and research activities from CebrianLab.
    design:
      columns: '1'

  - block: collection
    content:
      title: News
      count: 5
      filters:
        folders:
          - post
    design:
      view: compact
      columns: '1'

  - block: collection
    content:
      title: Events
      count: 5
      filters:
        folders:
          - event
    design:
      view: compact
      columns: '1'
---
