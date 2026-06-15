---
title: "Amazon Keyspaces now returns CDC iterator position in GetRecords response"
url: "https://aws.amazon.com/about-aws/whats-new/2026/06/keyspaces-cdc-iterator-position/"
date: "2026-06-03"
author: "aws@amazon.com"
feed_url: "https://aws.amazon.com/rss/"
---
Amazon Keyspaces now returns an iterator position in the GetRecords response for change data capture (CDC) streams, indicating whether consumers have reached the tip or if additional records are available. This enables optimization of polling frequency to reduce CDC consumption costs and improve streaming efficiency.
