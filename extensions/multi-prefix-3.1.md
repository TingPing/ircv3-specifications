---
layout: default
---

multi-prefix Client Capability Extension
----------------------------------------

Copyright (c) 2012 William Pitcock <nenolod@atheme.org>.

Unlimited redistribution and modification of this document is allowed provided
that the above copyright notice and this permission notice remains in tact.

The multi-prefix Client Capability
----------------------------------

When requested, the multi-prefix client capability will cause the IRC server to send
all possible prefixes which apply to a user in NAMES and WHO output.

These prefixes MUST be in order of 'rank', from highest to lowest.

