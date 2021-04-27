---
layout: post
title: New kivik CLI tool
date: 2021-04-27
author: Jonathan Hall
permalink: /kivik-cli-pre-release
---
I'm happy to announce a new experimental CLI tool, `kivik`, which is designed to simplify interaction with CouchDB servers.

Feel free to grab the most recent binaries from the [releases](https://github.com/go-kivik/xkivik/releases) page and try it out, or read the [documentation](https://github.com/go-kivik/xkivik/blob/master/cmd/kivik/README.md).

## Motivation

While debugging, experimenting with, or administrating CouchDB, I found the repetitive use of long `curl` commands to be toilsome. I've also found the flexibliyt of tools like `kubectl` to be informative (i.e. supporting both JSON, YAML, and arbitrary output formats). And finally, I have often longed for a simple CouchDB analog to tools like `pg_dump` and `pg_restore`.

This tool aims to satisfy all of these itches.

## Key features

- Easier to use than `curl` for interacting with CouchDB
- Supports both JSON and YAML inputs
- Supports JSON, YAML, and custom template outpus
- Allows replication between filesystem directories and CouchDB servers
- Supports retrys, to easily detect when a server becomes available

## Development status

While I believe the features most likely to be useful are implemented, some features are still completely unimplemented (see the [TODO list](TODO.md)). There are also likely bugs, as well as inconsistencies. [Bug reports](https://github.com/go-kivik/xkivik/issues) are very welcome!

All feedback is welcome!
