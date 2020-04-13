# Principles 

Eliminate hard/insesantly work
Service level objectives 
Automation
Release engineering
Simplicity

# Embracing risk

## Managing risk

The cost of redundant machine/compoute resources

the opportunity cost

## Measuring service risk

availability = uptime / (uptime + downtime)

request success rate

Aggregate availability 

availability = successsful requests / total_request

## Cost 

Proposed improvements in avail from 99.9 to 99.99

proposed increase in avail 0.09%

service revenue 1M

value of improved avail: 1M * 0.0009 = $ 900

one way of managing services cost effectively 


## Service level objectives

What are the behaviours that really matter? how to measure and evaluate those behaviours?

## Indicators

A crafully defined quantitative measure of some aspect of the level of service.

Most services consider request latency(how long it takes to return a response to a request), error rate(fraction of the received requests), system throughput (request per seconds)

## Objectives

A target value or range measured by an indicator. SLI <= target, or lower bound <= SLI <= upper bound.

Its complex to set, you can say u want average lantency under 100 milliseconds.

## agreements

what happens if the SLO is not met? if no consequences you are looking at SLO


## indicators in practice

what metrics are meaningful to your system?

choose just a few metrics but dont leave behaviours unexamined.

User-facing serving systems care about availability, latency and thoughput.

Storage systems -> latency, avail, durability

bid data systems -> throughput, end to end latency

All SYSTEMS CARE ABOUT CORRECTNESS, this is not mainly sre jobs

## collecting indicators 

Collecting indicators in percentiles 

50th, 85th, 95th percentile of the 

## Standardize Indicators
We recommend that you standardize on common definitions for SLIs so that you don’t have to reason about them from first principles each time. Any feature that conforms to the standard definition templates can be omitted from the specification of an individual SLI, e.g.:

Aggregation intervals: “Averaged over 1 minute”

Aggregation regions: “All the tasks in a cluster”

How frequently measurements are made: “Every 10 seconds”

Which requests are included: “HTTP GETs from black-box monitoring jobs”

How the data is acquired: “Through our monitoring, measured at the server”

Data-access latency: “Time to last byte”

## Objectives in practice 

find about what users care about no what you can measure.

Its found that its better to define objective and walk back to define indicators.

## examples 

- 99 % of Get RPC calls will complete in less than 100ms

If shape of performance curves are importan then you can define multiple SLOs

- 90 % of Get RPC calls wil lcomplete in less thaan 1 ms.

- 99 % of the Get RPC calls will complete in less than 10 ms

- 99.9% of Get RPC calls will complete in less than 100ms

if there are heterogenious workloads we can define the following:

- 95% of the throughput clients set RPC calls will complete in < 1s 

- 99% of the latency clients set RPC calls with payloads < 1Kb will complete in < 100 ms

Keep track of SLOs against the error budget in a weekly or daily basis.

## Choosing targets 

dont pick a target based on current performance

keep it simple

avoid absolutes

Have as few SLOs as possible

perfection can wait

## Control Measures

1. Monitor and measure the system’s SLIs.
2. Compare the SLIs to the SLOs, and decide whether or not action is needed.
3. If action is needed, figure out what needs to happen in order to meet the target.
4. Take that action.

SLOs set expectations

Keep a safety margin

dont overachieve




