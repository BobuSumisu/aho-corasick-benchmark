# Aho-Corasick Benchmark

Inspired by [anknown](https://github.com/anknown/ahocorasick) I wanted to see
how my [Aho-Corasick
implementation](https://github.com/BobuSumisu/aho-corasick) compared to others'.

I created a simple [benchmark](main.go) and ran it on my laptop.

With 512,000 patterns, my implementation has comparable build time and faster
search time than the other implementations:

          name    patterns         build     search    matches       alloc
    anknown         512000     1470.74ms    16.20ms      94000    27.94GiB
    bobusumisu      512000      707.74ms    11.12ms      94000    30.03GiB
    cloudflare      512000    41318.84ms     4.39ms       4490    53.71GiB
    iohub           512000      568.90ms    17.86ms      91986    54.08GiB

[cloudflare](https://github.com/cloudflare/ahocorasick) is implemented a bit
differently though. It doesn't output position of matches but returns indices
into the original patterns array.

![benchmark plot](benchmark.png)
