---
slug: /alerts/webhook-connections/servicenow
title: ServiceNow
description: With the ServiceNow integration, search results from Sumo Logic can be uploaded to your organization's ServiceNow account.
---

import useBaseUrl from '@docusaurus/useBaseUrl';

Your organization can use collected data to investigate issues across your deployment.

Data is uploaded to ServiceNow via the use of scheduled searches. After saving a search, results are available in ServiceNow. Additionally, you can launch ad-hoc ServiceNow investigations using search results in Sumo Logic.

To access [ServiceNow connections](/docs/alerts/webhook-connections/servicenow/), go to **Manage Data** > **Monitoring** > **Connections**.<br/><img src={useBaseUrl('img/connection-and-integration/connections.png')} alt="connections" />

From here, you can also:
* **Search Connections** to search. 
* **Edit** Connections. 
* **Delete** Connections. 
* View the **Details** of Connections.

* To create events in ServiceNow, see [Set Up ServiceNow Connections](/docs/alerts/webhook-connections/servicenow/set-up-connections).
* To create incidents in ServiceNow, see [Set Up a ServiceNow Incident Webhook Connection](/docs/alerts/webhook-connections/servicenow/set-up-security-incident-webhook).
* To import and maintain real-time information about AWS and VMware virtual machine assets into the ServiceNow CMDB, see the [Service Graph Installation and Configuration Guide](https://store.servicenow.com/appStoreAttachments.do?sys_id=d06467ab1bdab4d051a62132604bcb5e).
* For the Sumo Logic Cloud SIEM Enterprise (CSE) integration with the ServiceNow Security Incident Response (SIR) module, see [Security Incident Response (SIR) Integration](../../../cse/integrations/security-incident-response-integration.md).

import DocCardList from '@theme/DocCardList';
import {useCurrentSidebarCategory} from '@docusaurus/theme-common';

In this section, we'll introduce the following concepts:

<DocCardList items={useCurrentSidebarCategory().items}/>
