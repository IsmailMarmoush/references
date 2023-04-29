# Observability

## Introduction

* [Know your app: Add metrics to Java with Micrometer](https://www.youtube.com/watch?v=ldeb_DaH49U)
* [Understanding Prometheus Metric Types | Meaning and Usage (Gauge, Counter, Summary, Histogram)](https://www.youtube.com/watch?v=fhx0ehppMGM)
* [Tom Gregory YouTube: The 4 Types Of Prometheus Metrics](https://www.youtube.com/watch?v=nJMRmhbY5hY)
* [Tom Gregory Article](https://tomgregory.com/the-four-types-of-prometheus-metrics/)
* https://prometheus.io/docs/practices/histograms/
* https://www.youtube.com/watch?v=SYO-LmA647E

# METL

* Metrics, Events, Traces and Logs

# 1.0 Metrics

* System Metrics (CPU, Memory, Disk)
* Infrastructure metrics (e.g AWS cloudwatch)
* Web tracking scripts (e.g Google Analytics)
* Application metrics (APM, Error tracking)
* Business metrics(e.g customer signups)
* Consist of (Timestamp, Name, Value, Dimensions)

## Counters

* Used for
    * Values that increases only (not values that decrease) so it's only incrementation
* Examples
    * Number of error happened in past 2 hours
    * number of requests processed
* It's useful to calculate the speed of how value is increasing (rate)
* Prometheus: rate(metric_name[5m])

## Gauges

* Used for
    * Values that go up and down
* Examples
    * Memory usage
    * Thread Queue size
    * Number of **current in progress** tasks
* Rate doesn't work here
* Prometheus: avg_over_time(metric_name[5m])

## Histograms

* Used for
    * Frequency of value observations that fall into specific defined buckets
* Used when
    * The range of values (buckets) are somehow known upfront
    * You don't care what the actual values are and happy with averages and approximations
* Buckets and Percentile/quantile
    * Calculated on the Prometheus server side
    * The φ-quantile is the observation value that ranks at number φ*N among the N observations. Examples for
      φ-quantiles:
        * The 0.5-quantile is known as the median. The 0.95-quantile is the 95th percentile.
    * .005, .01, .025, .05, .075, .1, .25, .5, .75, 1, 2.5, 5, 7.5, 10. This is very much tuned to measuring request
      durations below 10 seconds, so if you’re measuring something else you may need to configure custom buckets.
    * All buckets are accumulative and adding +1 to one buckets adds +1 to all larger ones
* Examples
    * Request durations for specific endpoint,
    * Response sizes
* Prometheus:
    * `rate(<metric_name>_sum[5m])/rate(<metric_name>_count[5m])`
    * `histogram_quantile(0.95, sum(rate(request_duration_bucket[5m])) by (le))`

## Summaries

* Very similar to histograms but
* Buckets and Percentile/quantiles
    * Calculated on the Application server side, therefore it can't be aggregated from number of application instances
* Used for
    * Calculating accurate quantiles
* Used when
    * The range of values are not known up front
* Examples
    * Request durations
    * Response size
* Prometheus:
    * `rate(<metric_name>_sum[5m])/rate(<metric_name>_count[5m])`
    * `request_duration_summary{quantile="0.95"}`


## 2.0 Logs

* Plain text, Structured, binary
* System & server logs (syslog)
* Fireware & network system logs
* Application (log4j)
* Platform & server logs (apache, nginx, databases)