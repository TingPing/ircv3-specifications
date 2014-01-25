---
layout: default
---

# IRC `BATCH` extension

Copyright (c) 2012 William Pitcock <nenolod@dereferenced.org>.

Unlimited redistribution and modification is allowed provided that the above
copyright notice and this permission notice remains intact.

## The `batch` client capability

This extension describes a capability which causes a new verb to be sent to
clients when the IRC server wishes to designate that a series of events are
related to each other.

Use-cases include visual suppression of netsplits and netjoins. 

The name of this client capability MUST be named `batch`.

## The `BATCH` verb

The IRC server will send a `BATCH` verb when it wants the client to begin
batching events together, and send another `BATCH` verb when the transaction
is concluded.

The following syntax MUST be used when starting a batch:

	BATCH +reference-tag

The following syntax MUST be used when ending a batch:

	BATCH -reference-tag

Reference tag MUST contain only ASCII letters, numbers, and/or hyphen, and MUST be case-sensitive.

The batched events MUST use `batch` message tag refering to the batch's reference tag.

`BATCH` verb itself MUST NOT have `batch` message tag.

Client SHOULD start processing the batched events only when received the end of the batch.

## Example

Here is an example of the BATCH verb being used:

	:irc.server.net BATCH +yXNAbvnRHTRBv
	@batch=yXNAbvnRHTRBv :nenolod!nenolod@localhost QUIT :*.net *.split
	@batch=yXNAbvnRHTRBv :jilles!jilles@localhost QUIT :*.net *.split
	:irc.server.net BATCH -yXNAbvnRHTRBv

The client could then realize that both nenolod and jilles quit due to a
netsplit without having to guess.

