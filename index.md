![sohonet logo](images/sohonetlogo.png "sohonet logo")

# Labs

Open source code from sohonet.

## Nameko StatsD

[nameko.statsd](nameko.statsd.md) integrates Nameko with StatsD.


## Nameko Eventlog Dispatcher

[nameko eventlog dispatcher](nameko.eventlog.dispatcher.md) is a dependency provider to aid with logging events in nameko.


## Miko

[miko](miko.md) is about making RPC requests from javascript to nameko.

## CISE-ELK

[CISE.ELK](CISE.elk.md) contains all the logstash and pmacctd configs, elasticsearch index templates, kibana dashboards and elastalert alerting rules created for the CISE project. It represents an entire configured ELK stack which can be used to record and report on security relevant events for your infrastructure.

## Generate-ipdatabase

Populate Elastic Search with [FireHOL](http://iplists.firehol.org/) ip lists.
[repo](https://github.com/sohonetlabs/generate-ipdatabase). To be used with Ciseipdb Logstash Plugin

## Ciseipdb Logstash Plugin

This plugin allows you to search for matching IPs in Elasticsearch IP database indexes and add that information into events. [repo](https://github.com/sohonetlabs/logstash-filter-ciseipdb)

## fourcc.js

Json format of the fourcc.

FOURCC is short for "four character code" - an identifier for a video codec, compression format, colour or pixel format used in media files. [repo](https://github.com/sohonetlabs/fourcc.js)

