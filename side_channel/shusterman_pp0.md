## Background

Find the GitHub repo [here](https://github.com/Yossioren/pp0) and more background
[here](https://orenlab.sise.bgu.ac.il/p/PP0).

## Insights

## Approaches

The basic methodology is website fingerprinting, where memorygrams are collected for
inference of visited websites.

Cache occupancy channel is used instead of Prime+Probe. This channel is less fine-grained
and is used due to low timing resolution. Sweep counting has even lower accuracy.

A deep neural network is used as classifier.

DNS Racing assumes a JavaScript engine that does not privide any timer. An external
timer is created by leveraging the predictability of a browser when accessing a
non-existent domain.

String and Sock uses operations on long HTML strings instead of JavaScript arrays.
It lets Javascript search for a non-existent substring within an LLC-length string.
A malicious WebSocket server is used for timing the searching.

CSS Prime+Probe requires no Javascript at all. It is built upon String-and-Sock.

## Takeaway

## Questions
