---
id: osquery
title: Osquery - Cloud SIEM
sidebar_label: Osquery
description: Configure an HTTP source to ingest osquery log messages and send them to the osquery system parser.
---

This section has instructions for collecting [osquery](https://osquery.io/) log messages  and sending them to Sumo Logic to be ingested by CSE.

Sumo Logic CSE supports osquery logs sent in JSON format for the following log types:

* Schedule results in Events format
  :::note
  Batch and Snapshot formats are not natively supported.
  :::
* Process Auditing
* Anomaly Detection
* File Integrity Monitoring

## Configure collection

In this step, you configure an HTTP Source to collect osquery log messages. You can configure the source on an existing Hosted Collector or create a new collector. If you’re going to use an existing collector, jump to Configure an HTTP Source below. Otherwise, create a new collector as described in Configure a hosted  collector below, and then create the HTTP Source on the collector.

### Configure a hosted collector

1. In Sumo Logic, select **Manage Data > Collection > Collection**.
1. Click **Add Collector**.
1. Click **Hosted Collector**.
1. The **Add Hosted Collector** popup appears.  
    ![add-hosted-collector.png](/img/cse/add-hosted-collector.png)
1. **Name**. Provide a Name for the Collector.
1. **Description**. (Optional)
1. **Category**. Enter a string to tag the output collected from the source. The string that you supply will be saved in a metadata field  called `_sourceCategory`. 
1. **Fields**. 
    1. If you are planning that all the sources you add to this collector will forward log messages to CSE, click the **+Add Field** link, and add a field whose name is `_siemForward` and value is *true*. This will cause the collector to forward all of the logs collected by all of the sources on the collector to CSE.
    1. If all sources in this collector will be osquery sources, add an additional field with key `_parser` and value */Parsers/System/Osquery/Osquery JSON*.
    :::note
    It is also possible to configure individual sources to forward to CSE, as described in the following section.
    :::

### Configure an HTTP Source

1. In Sumo Logic, select **Manage Data > Collection > Collection**. 
1. Navigate to the Hosted Collector where you want to create the source.
1. On the **Collectors** page, click **Add Source** next to a Hosted Collector.
1. Select **HTTP Logs & Metrics**. 
1. The page refreshes.  
    ![http-source.png](/img/cse/http-source.png)
1. **Name**. Enter a name for the source. 
1. **Description**. (Optional) 
1. **Source Host**. (Optional) Enter a string to tag the messages collected from the source. The string that you supply will be saved in a metadata field called `_sourceHost`.
1. **Source Category**. Enter a string to tag the output collected from the source. The string that you supply will be saved in a metadata field called `_sourceCategory`.
1. **SIEM Processing**. Click the checkbox to configure the source to forward log messages to CSE.
1. **Fields**. If you are not parsing all sources in the hosted collector with the same parser, **+Add Field** named `_parser` with the value `/Parsers/System/Osquery/Osquery JSON.`
12. **Advanced Options for Logs**. For information about the optional advanced options you can configure, see HTTP Logs and Metrics Source.
13. Click **Save**.
14. Make a note of the HTTP Source URL that is displayed. You’ll supply it in when you configure osquery in the next section.

## Configure an Osquery log profile

In this step you configure osquery to send log messages to CIP. For instructions, see [Logging osquery](https://osquery.readthedocs.io/en/stable/deployment/logging/) in osquery help.

## Verify ingestion

In this step, you verify that your logs are successfully making it into CSE. 

1. Click the gear icon, and select **Log Mappings** under **Incoming Data**.  
    ![log-mappings-link.png](/img/cse/log-mappings-link.png)
1. On the **Log Mappings** page, search for *osquery* and check under **Record Volume**.
1. For a more granular look at the incoming records, you can also search Sumo Logic for osquery Records.  
    ![osquery-record-volume.png](/img/cse/osquery-record-volume.png)
