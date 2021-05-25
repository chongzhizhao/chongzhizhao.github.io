## Intel

It seems that starting from Skylake Intel has implemented non-inclusive LLC in server-grade
[Xeon](https://software.intel.com/content/www/us/en/develop/articles/intel-xeon-processor-scalable-family-technical-overview.html)
[processors](https://software.intel.com/content/www/us/en/develop/articles/intel-xeon-processor-scalable-family-technical-overview.html).
Detail information is [here](https://en.wikichip.org/w/images/0/0d/intel_xeon_scalable_processor_architecture_deep_dive.pdf).
In this case, the L2 is inclusive of L1, but L3 is non-inclusive. Potentially, from
[Willow Cove](https://www.anandtech.com/show/15971/intels-11th-gen-core-tiger-lake-soc-detailed-superfin-willow-cove-and-xelp/3)
even L2 cache might not be inclusive.

## AMD

They have been doing inclusive L2 and non-inclusive L3 since
[the dawn of time](https://www.anandtech.com/show/15971/intels-11th-gen-core-tiger-lake-soc-detailed-superfin-willow-cove-and-xelp/3).
