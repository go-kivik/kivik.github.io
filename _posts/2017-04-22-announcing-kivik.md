---
layout: post
title: Announcing Kivik
subtitle: The general-purpose CouchDB client API for Go and GopherJS
date: 2017-04-22
author: Jonathan Hall
permalink: /announcing-kivik-couchdb-pouchdb-golang
excerpt: For nearly 3 months I've been working on a Golang client library for CouchDB and PouchDB. Announcing: Kivik 1.0.
---

<i>**Editorial Note:** This post originally appeared on
[Jonathan Hall's blog](http://verbally.flimzy.com/announcing-kivik-couchdb-pouchdb-go/).</i>

For nearly 3 months now, I’ve spent most of my free time working on a new
open-source project: a Go client library for CouchDB and PouchDB. As I’m now
putting together the last major feature for a 1.0 release, I feel it’s time to
make my work public.

<img alt="Kivik logo" src="/img/logo-kivik-lg.png" sizes="(max-width: 300px) 100vw, 300px"
    height="248" width="300" style="float: right;">
So today I am announcing [Kivik](https://github.com/flimzy/kivik)!

> Kivik is a general-purpose client API for the
> [Apache CouchDB](http://couchdb.apache.org/) database, and
> similar databases (such as [PouchDB](https://pouchdb.com/)) for
[Go](https://golang.org/) and [GopherJS](http://gopherjs.org/).

### What Kivik currently provides that other libraries don't

- **Kivik provides a backend-agnostic CouchDB client API.**  Similar to the
 standard library’s sql package, different backend drivers can be substituted at
 build time, with no change to the client code. At the moment two backend
 drivers are supported, one for CouchDB, and one for PouchDB.
- **Kivik supports both Go and GopherJS.** For GopherJS, Kivik provides PouchDB
 bindings, so that GopherJS programs can use the same client API as standard Go
 programs. Previously, it was necessary to use different client libraries for Go
 (i.e. [github.com/fjl/go-couchdb](https://godoc.org/github.com/fjl/go-couchdb))
 and PouchDB ([github.com/flimzy/go-pouchdb](https://github.com/flimzy/go-pouchdb)).
- **Kivik provides an unambiguous open-source license.** The leading Go CouchDB
 library, [github.com/fjl/go-couchdb](https://godoc.org/github.com/fjl/go-couchdb),
 has no published license, which probably means it’s not open-source (but IANAL).
 Kivik is released under the
 [Apache License](https://github.com/flimzy/kivik/blob/master/LICENSE.md), for
 complete open-source compatibility with CouchDB and PouchDB.
- **Kivik provides support for both CouchDB 1.6.x and CouchDB 2.0.x.** To my
 knowledge, no other Go client library provides support for MongoDB-style
 queries, which were added in CouchDB 2.0, or support for any of the other
 [API changes](http://docs.couchdb.org/en/2.0.0/whatsnew/2.0.html#version-2-0-0)
 introduced in 2.0.0. Kivik aims to remedy that, by providing a client API that
 works with both 1.6.x servers and 2.0.x servers (as well as future releases).
- **Kivik provides row iterators.** All other Go CouchDB libraries I have seen
 require reading an entire result set before parsing or returning any rows. For
 large result sets, this is a huge waste of memory, not to mention slow. Kivik
 provides iterators over common query results, just as the sql package does, so
 you can begin using your results, even while the HTTP response is still in
 transit.

### Future development plans include

- **Kivik will provide a memory-based driver.** The purpose of this driver is to
 facilitate automated testing, without requiring running a CouchDB server. Just
 connect to the memory driver, and unit-test away!
- **The `kivik` command-line tool.** It already exists, but does little of value
 yet. In the future, it will provide a simple way to fire up a memory-backed
 server, which will allow for lightweight unit/integration tests, without the
 need for a full CouchDB server.
- **Add full replication support to Kivik.** At present, Kivik can initiate a
 replication via either the CouchDB `_replicator` database, or PouchDB’s
 `replicate()`` function, but has no understanding of the replication protocol
 itself. In the future, Kivik will also be able to do replications itself. This
 will allow replicating between backends (such as from the `memory` backend to
 the `CouchDB` backend), which could facilitate seeding of databases, and other
 scenarios.

### Current development status

As of this writing, the client library is considered 1.0-feature-ready except
for the addition of replication, which is nearing completion (2-3 days more, max).

I welcome testers to use the client library and provide bug reports and/or pull
requests. I’ll be doing my own testing in a couple of my own apps for the next
few weeks.

I hope to make an official 1.0.0 release on or around June 1.

After 1.0.0 is out the door, my next task will be completing the `memory`
backend driver, to facilitate automated testing applications.

### Why the name Kivik?

[Kivik](https://en.wikipedia.org/wiki/Kivik) is a locality situated in
Simrishamn Municipality, Skåne County, Sweden with 960 inhabitants as of 2010.

It also happens to be, by sheer coincidence, I’m sure, the name of a
[line of sofas from IKEA](http://www.ikea.com/us/en/catalog/categories/series/18329/).
Also by coincidence, it’s the shortest name of an IKEA sofa line that can be
spelled using only Latin characters.

It also happens to be a palindrome, which I’m sure someone will appreciate
immensely.

### Volunteers welcome

If you find Kivik useful or intriguing, you can help in any of the following
ways:

- **Testing** At this stage, the most valuable thing you can offer is simply
 using and testing Kivik, and reporting bugs.
 - **Pull requests** Pull requests to accompany bug reports (or feature
 requests) are of course welcome, too! I encourage you to open an issue before
 submitting PRs for new features, to discuss the implications.
- **Logo design** The “logo” I’m using is just a public domain image. If you’re
 graphically inclined, I’d love a custom logo. Please contact me by creating an
 [issue on GitHub](https://github.com/flimzy/kivik/issues/new) if you are
 interested.
