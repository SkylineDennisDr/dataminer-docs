---
uid: General_Main_Release_10.4.0_CU6
---

# General Main Release 10.4.0 CU6 - Preview

> [!IMPORTANT]
> We are still working on this release. Some release notes may still be modified or moved to a later release. Check back soon for updates!

> [!TIP]
> For information on how to upgrade DataMiner, see [Upgrading a DataMiner Agent](xref:Upgrading_a_DataMiner_Agent).

### Enhancements

#### SLAnalytics: Alarms and suggestion events for virtual functions will now be generated on the parent element [ID_39707]

<!-- MR 10.4.0 [CU6] - FR 10.4.9 -->

When, in the scope of behavioral anomaly detection, proactive cap detection or pattern matching, SLAnalytics has to generate alarms or suggestion events for virtual functions, from now on, it will generate them on the parent element. However, it will continue to generate alarms and suggestion events for all other kinds of DVEs on the child element.

#### NATS configuration can now be reset by calling an endpoint of SLEndpointTool.dll [ID_39871]

<!-- MR 10.4.0 [CU6] - FR 10.4.8 -->

From now on, the NATS configuration can be reset by calling the following endpoint in e.g. an Automation script:

`SLEndpointTool.Config.NATSConfigManager.ResetNATSConfiguration()`

### Fixes

#### SLNet - CloudEndpointManager: Problem at startup when NATS and NAS services were not installed [ID_39980]

<!-- MR 10.3.0 [CU18]/10.4.0 [CU6] - FR 10.4.9 -->

At startup, in some cases, the CloudEndpointManager in SLNet could throw an exception when the NATS and NAS services were not installed.