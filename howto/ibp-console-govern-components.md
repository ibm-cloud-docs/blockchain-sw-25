---

copyright:
  years: 2019, 2020
lastupdated: "2020-06-15"

keywords: network components, Kubernetes, OpenShift, allocate resources, batch timeout, reallocate resources, LevelDB, CouchDB, ordering nodes, ordering, add and remove, governance

subcollection: blockchain-sw-25

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}
{:important: .important}
{:tip: .tip}
{:pre: .pre}

# Managing deployed components
{: #ibp-console-govern-components}

<div style="background-color: #f4f4f4; padding-left: 20px; border-bottom: 2px solid #0f62fe; padding-top: 12px; padding-bottom: 4px; margin-bottom: 16px;">
  <p style="line-height: 10px;">
    <strong>Running a different version of IBM Blockchain Platform?</strong> Switch to version
    <a href="https://cloud.ibm.com/docs/blockchain-sw?topic=blockchain-sw-ibp-console-govern-components">2.1.2</a>,
    <a href="https://cloud.ibm.com/docs/blockchain-sw-213?topic=blockchain-sw-213-ibp-console-govern-components">2.1.3</a>
    </p>
</div>


After creating CAs, peers, and ordering nodes, you need to monitor the resources used by the nodes and potentially reallocate resources.
{:shortdesc}

**Target audience:** This topic is designed for network operators who are responsible for creating, monitoring, and managing their components in the blockchain network.

## Considerations when reallocating resources
{: #ibp-console-govern-components-reallocate-resources}

Resizing a node requires the containers to be rebuilt, which can cause a delay in the functioning of the node.
{:important}



Third party tools such as [Sysdig](https://sysdig.com){: external} can be used to help monitor the usage in your cluster. If you determine that a worker node is running out of resources, you can add a new larger worker node to your cluster and then delete the existing working node.
{:note}


While it takes less effort to deploy enough resources to your Kubernetes cluster from the start and therefore be able deploy and expand resources without having to increase the resources in your cluster, the bigger the deployment, the more it will cost. Users need to consider their options carefully and recognize the tradeoffs that they are making regardless of the option that they choose.




You can scale your cluster by monitoring your nodes and following the instructions available from your cloud provider to add more nodes, larger nodes, or increasing the size of the nodes, depending on the options available in your cloud provider. The method you will use to increase storage will depend on the storage class you chose for your cluster. Note that if you are about to exhaust the storage on your peer or ordering node, you might need to deploy a new peer or ordering node with more storage and let it sync via your other components on the same channels.


Note that you do not need to adjust the CPU, memory, or storage for your smart contract pods. These pods will automatically use as many resources as they need to function efficiently. In cases where your smart contracts are struggling because of insufficient resources, you will have to address this at the cluster level.
{: tip}



## Deleting components
{: #ibp-console-govern-components-delete}

{[pg-deleting-components.md]}

