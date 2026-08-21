---
layout: page
title: MomenTag
description: A tag-based photo management app — Django backend, Jetpack Compose client
importance: 3
category: systems
---

**September 2025 – December 2025**

A photo management application organized around tags rather than folders, built from scratch as a full-stack project.

- **Backend** — a RESTful API in **Django**, covering the data model, authentication, and tag query endpoints
- **Frontend** — a native Android client in **Kotlin** with **Jetpack Compose**

Most of my work sits well below the application layer, so this was a deliberate step in the other direction: designing an API that someone else has to consume, and then being that someone. Having to write both halves made it obvious how quickly a convenient-looking endpoint becomes awkward on the client side.
