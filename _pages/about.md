---
layout: about
title: about
permalink: /
subtitle: Undergraduate Researcher, TNET Lab · Dept. of Computer Science and Engineering, <a href="https://cse.snu.ac.kr/en">Seoul National University</a>

profile:
  align: right
  image: prof_pic.jpg
  image_circular: false # crops the image to make it circular
  more_info: >
    <p>TNET Lab</p>
    <p>Dept. of Computer Science and Engineering</p>
    <p>Seoul National University</p>

selected_papers: false # includes a list of papers marked as "selected={true}"
social: true # includes social icons at the bottom of the page

announcements:
  enabled: false # includes a list of news items
  scrollable: true # adds a vertical scroll bar if there are more than 3 news items
  limit: 5 # leave blank to include all the news in the `_news` folder

latest_posts:
  enabled: false
  scrollable: true # adds a vertical scroll bar if there are more than 3 new posts items
  limit: 3 # leave blank to include all the blog posts
---

I am an undergraduate in Computer Science and Engineering at **Seoul National University**, and a research intern at the **TNET Lab**.

My interest sits at the boundary between the network stack and the hardware underneath it — the places where a clean abstraction turns out to cost real CPU cycles. At TNET I work on [**DPUmesh**](/projects/), a service mesh that moves sidecar proxying off the host and onto a BlueField-3 DPU, so that microservice communication stops competing with the application for CPU. I integrated the architecture directly into the Thrift RPC framework, which lets existing services adopt the offloaded data path without changing a line of user code.

Before that I wrote an [x86-64 compiler](/projects/) for a small language, from the lexer through to register allocation, in C. Having built both a compiler backend and a network data path, I have come to think of them as the same kind of problem: deciding what work happens where, and paying attention to what that choice costs.

I am currently looking toward **distributed systems** and **kernel-bypass networking** for graduate study. If you are working on something in that space, I would be glad to hear about it — my email is below.
