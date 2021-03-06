---

copyright:
  years: 2020
lastupdated: "2020-06-03"

keywords: metering, licensing service, license consumption, license tracking

subcollection: blockchain-sw-25

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:api: .ph data-hd-interface='api'}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: data-hd-programlang="c#"}
{:cli: .ph data-hd-interface='cli'}
{:codeblock: .codeblock}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:fuzzybunny: .ph data-hd-programlang='fuzzybunny'}
{:generic: data-hd-operatingsystem="generic"}
{:generic: data-hd-programlang="generic"}
{:gif: data-image-type='gif'}
{:go: .ph data-hd-programlang='go'}
{:help: data-hd-content-type='help'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:important: .important}
{:ios: data-hd-operatingsystem="ios"}
{:java: .ph data-hd-programlang='java'}
{:java: data-hd-programlang="java"}
{:javascript: .ph data-hd-programlang='javascript'}
{:javascript: data-hd-programlang="javascript"}
{:new_window: target="_blank"}
{:note .note}
{:note: .note}
{:objectc data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:route: data-hd-keyref="route"}
{:row-headers: .row-headers}
{:ruby: .ph data-hd-programlang='ruby'}
{:ruby: data-hd-programlang="ruby"}
{:runtime: architecture="runtime"}
{:runtimeIcon: .runtimeIcon}
{:runtimeIconList: .runtimeIconList}
{:runtimeLink: .runtimeLink}
{:runtimeTitle: .runtimeTitle}
{:screen: .screen}
{:script: data-hd-video='script'}
{:service: architecture="service"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:service_name: data-hd-keyref="service_name"}
{:shortdesc: .shortdesc}
{:space_name: data-hd-keyref="space_name"}
{:step: data-tutorial-type='step'}
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:ui: .ph data-hd-interface='ui'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vbnet: .ph data-hd-programlang='vb.net'}
{:video: .video}
 
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:important: .important}
{:note: .note}
{:term: .term}
{:tip: .tip}
{:download: .download}


# Tracking license consumption
{: #metering}

<div style="background-color: #6fdc8c; padding-left: 20px; padding-right: 20px; border-bottom: 4px solid #0f62fe; padding-top: 12px; padding-bottom: 4px; margin-bottom: 16px;">
  <p style="line-height: 20px;">
    <strong>Important: You are not looking at the latest product documentation.  Make sure you are reading the documentation that matches the version of the software that you are using. Switch to product version </strong>
    2.5, <a href="/docs/blockchain-sw-251?topic=blockchain-sw-251-metering">2.5.1</a>,
    <a href="/docs/blockchain-sw-252?topic=blockchain-sw-252-metering">2.5.2 (latest)</a>
    </p>
</div>

This page describes the licensing service that can be used with the {{site.data.keyword.blockchainfull}} Platform to track license consumption. The License Service collects and measures the license usage of Virtual Processor Core (VPC) metric at the cluster level.
{:shortdesc}

## Overview
{: #metering-overview}

The integrated licensing solution collects and stores licensing information that can be used for audit purposes and for tracking license consumption in cloud environments and on premises. This solution works in the background and does not require any configuration. Only one instance of the license service is deployed per cluster regardless of the number of {{site.data.keyword.blockchainfull_notm}} Platform services and containerized programs that are installed on the cluster.

## Manual integration of License Service
{: #metering-manual-integration}

For instructions on how to manually install the License Service see the
[IBM licensing operator readme file](https://github.com/IBM/ibm-licensing-operator/blob/master/README.md){: external}

## Validating if License Service is deployed on the cluster

To ensure license reporting continuity for license compliance purposes, you need to confirm that the license service is successfully deployed and periodically verify that it is active by logging in to the cluster and running the following command:

```
kubectl get pods --all-namespaces | grep ibm-licensing | grep -v operator
```
{: codeblock}

If it is successfully deployed and running, you see output similar to:
```
1/1 Running
```

## Archiving license information data before you decommission the cluster
{: #metering-archive}

Before you decommission your cluster where the licensing service is running, you need to archive the license metric utilization evidence. Retrieve the audit snapshot for the period when it was running on the cluster and store it for audit purposes.

For more information about the licensing solution, see the [License Service documentation](https://www.ibm.com/docs/en/SSHKN6/license-service/1.x.x/license_service.html){: external}.
