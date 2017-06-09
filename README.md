# Grafana + InfluxDb based system for load test results

## Table of Contents
1. [Overview](#overview)
2. [Setting up InfluxDb](#setting-up-influxdb)
3. [Writing data to InfluxDb](#writing-data-to-influxdb)
4. [Setting up Grafana](#setting-up-grafana)
5. [Viewing data in Grafana](#viewing-data-in-grafana)

## Overview

This guide describes how to write time-series data (e.g. load test measurements) into InfluxDb and then visualise them in Grafana.

## Setting up InfluxDb

Installation instructions are well described (https://docs.influxdata.com/influxdb/v0.9/introduction/installation/), I've used *brew* to do the set up on MacBook Pro/OS X El Capitan 10.11.6. After the installation it can be started either as background service (more suitable for CI environment) or as a process (more suitable for dev environment/workstation).

For launching the CLI use *influxd* command.

## Writing data to InfluxDb

At first, we need to create a database and define the users who should have access to it.
```sh
> create database test_db
> create user test with password 'test'
> create user grafana with password 'grafana'
> grant all on test_db to test
> grant read on test_db to grafana
```

We will use *test* user to write the data, and *grafana* user to access it from Grafana.

There are several ways to write data:
- insert the data through the REST API (documentation: https://docs.influxdata.com/influxdb/v0.9/guides/writing_data/). We will use it to insert the data while running the tests.
- import a DB dump (documentation: https://docs.influxdata.com/influxdb/v0.9/sample_data/data_download/). This method is more suitable when we need to import existing results into the system.

## Setting up Grafana

TODO

## Viewing data in Grafana

TODO
