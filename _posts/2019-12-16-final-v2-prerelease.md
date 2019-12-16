---
layout: post
title: (Probably) final 2.0.0 pre-release, and v3 announcement
subtitle: Final preparations for v2.0.0 (and v3!)
date: 2019-12-16
author: Jonathan Hall
permalink: /final-v2-prerelease
excerpt: "v2.0.0 (and v3.0.0) is almost here"
---

Today I tagged what I expect to be the final pre-relese of all core Kivik packages:

- **kivik** -- [v2.0.0-pre3](https://github.com/go-kivik/kivik/releases/tag/v2.0.0-pre3)
- **couchdb** - [v2.0.0-pre4](https://github.com/go-kivik/couchdb/releases/tag/v2.0.0-pre4)
- **pouchdb** -- [v2.0.0-pre3](https://github.com/go-kivik/pouchdb/releases/tag/v2.0.0-pre3)
- **kivikmock** - [v2.0.0-pre3](https://github.com/go-kivik/kivikmock/releases/tag/v2.0.0-pre3) (unchanged)
- **kiviktest** - [v2.0.0-pre4](https://github.com/go-kivik/kiviktest/releases/tag/v2.0.0-pre4)

I expect to tag the final **v2.0.0** version within a couple of weeks, unless bug reports come in.

Here I would also like to announce that at roughly the same time, I intend to release **v3.0.0**. v3.0.0 will be identical to v2.0.0, except that it will support [Go modules](https://github.com/golang/go/wiki/Modules).  I could make that change along with the **v2.0.0** release, but this could stand to break anyone using a v2.0.0 pre-release, and although that wouldn't strictly violate the compatibility guarantee, since these are, after all, pre-releases, I believe it will be the smoothest upgrade path. And version numbers are free, after all!
