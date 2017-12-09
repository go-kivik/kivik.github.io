---
layout: post
title: Preparing for a Package Rename
date: 2017-12-09
author: Jonathan Hall
permalink: /preparing-for-rename
---

When I first wrote Kivik, I put everything into a single package. The core
library, the CouchDB and PouchDB drivers, and the experimental features I was
working on: A server, Memory driver, etc. This lead to quite a bloated package,
with a majority of the bloat being irrelevant to most users of the package.

In August, I began the process of
[splitting the package](https://github.com/flimzy/kivik/issues/178) into its
individual components. At the same time, I created a new
[GitHub organization](https://github.com/go-kivik) to organize all the
Kivik-related packages.  This transition is now nearly complete, with only one
major step remaining: Moving the core Kivik library to the new organization.

I have been slow in making this transition, because I believe it stands a high
chance of being painful for existing users of Kivik. Other Go projects have
made similar changes in the past, sometimes with
[less than stellar results](https://github.com/sirupsen/logrus/issues/570#issuecomment-313933276).
I want to avoid similar problems.

To this end, the strategy I intend to employ is detailed below.

## The plan

1. The `kivik` package and all sub-packages will be pinned (via
    [import comments](https://golang.org/cmd/go/#hdr-Import_path_checking)) to
    the old repository name (`github.com/flimzy/kivik`). This step has already
    [been completed](https://github.com/flimzy/kivik/pull/260).
2. The `kivik` repo will then be renamed, to live under the new organization as
    `github.com/go-kivik/kivik`. At this point, GitHub will redirect requests
    (including from `go get`) for `github.com/flimzy/kivik` to the new package,
    but the import comments will continue to require that the package be
    referenced by the old name. I will make this change in the coming week or
    two.
3. Subsequent releases of the 1.x series (to live in a new `1.x` branch),
    if any, will retain the import comments pinning the package to the old
    `github.com/flimzy/kivik` namespace.
4. The 2.x.x release of Kivik, which I expect to be forthcoming shortly, will
    replace the import comments to tag the repo to the new namespace of
    `github.com/go-kivik/kivik`.

This should allow me to couple the effectual package rename to the Kivik 2.x
release, which will include other breaking changes.

Once the 2.x work begins, consumers of Kivik will be required to use vendoring,
ideally with a semver-aware versioning tool such as
[dep](https://github.com/golang/dep) or
[glide](https://github.com/Masterminds/glide). But I think this is a reasonable
assumption for any modern, production Go code.

## TL;DR;

Moving forward, users of Kivik 1.x will continue to use
`github.com/flimzy/kivik` as their import path, even after the package rename.

Users of Kivik 2.x will use the new import path of `github.com/go-kivik/kivik`.

## Questions?

If there are questions or comments about this, I encourage you to send your
feedback or suggestions by
[submitting an issue on GitHub](https://github.com/flimzy/kivik/issues/new).
