---
uid: Behavioral_anomaly_detection
---

# Behavioral anomaly detection

> [!TIP]
> This section contains information about behavioral anomaly detection in the Alarm Console. For more information on the functionality of this feature in general, see [Working with behavioral anomaly detection](xref:Working_with_behavioral_anomaly_detection).

Whenever behavioral anomaly detection finds an anomalous level shift, trend change, variance change, or flatline for a parameter, a "suggestion event" is generated in the Alarm Console.

These suggestion events can be viewed in a dedicated suggestion events tab, as alarms with severity "Information" and source "Suggestion Engine”. See [Adding and removing alarm tabs in the Alarm Console](xref:ChangingTheAlarmConsoleLayout#adding-and-removing-alarm-tabs-in-the-alarm-console).

You can also configure alarm templates to have alarms generated instead of suggestion events, depending on the parameter and the type of anomaly. See [Configuring Augmented Operations alarm settings](xref:Configuring_anomaly_detection_alarms).

From DataMiner 10.4.11/10.5.0 onwards<!--RN 39945-->, you can [provide feedback on suggestion events and alarms](xref:Providing_user_feedback) generated by behavioral anomaly detection. This feedback helps DataMiner improve its ability to decide when to trigger suggestion events or alarms. Prior to DataMiner 10.3.0 [CU20]/10.4.0 [CU8]/10.4.11, only the change point history of a parameter is considered when labeling behavioral anomalies.

Please note the following regarding suggestion events:

- Currently, no suggestion events are generated for outliers and unlabeled change points.

- Suggestion events generated to indicate a behavioral anomaly are automatically cleared 2 hours after their creation time or their last update time. From DataMiner 10.2.11/10.3.0 onwards, they are also cleared in case a new behavioral change is detected that ends the previous anomalous behavioral change. For example, when an alarm was created for an anomalous level increase at 1 PM, and a behavioral change point is detected at 2 PM when the level drops again, then the alarm created at 1 PM will be closed at 2 PM.

- Suggestion events generated to indicate a behavioral anomaly for [dynamic virtual elements](xref:Dynamic_virtual_elements) are generated on the child element. However, from DataMiner 10.3.0 [CU18]/10.4.0 [CU6]/10.4.9 onwards<!--RN 39707-->, suggestion events for [virtual functions](xref:srm_definitions#virtual-function) are generated on the parent element. Prior to DataMiner 10.3.0 [CU18]/10.4.0 [CU6]/10.4.9, these suggestion events are generated on the child element as well.

- Depending on the DataMiner version, different limitations are in place as to how many suggestion events can be generated for anomalous behavioral changes:

  - From DataMiner 10.4.0 [CU2]/10.4.5 onwards<!-- RN 39256 -->, at most 500 suggestion events related to behavioral anomaly detection can be shown in the active suggestion events tab of the Alarm Console.
  - From DataMiner 10.4.0 [CU1]/10.4.4 onwards<!-- RN 38674 -->, at most 50 new suggestion events per hour per type of anomaly (i.e. level shift, trend change, flatline, or variance change) can be generated per DataMiner Agent. There is no limit to the maximum number of anomaly alarm events, i.e. alarm events for parameters that have explicit [anomaly alarm monitoring configured in the alarm template](xref:Configuring_anomaly_detection_alarms).
  - From DataMiner 10.2.11/10.3.0 onwards, suggestion events are only created for the most significant changes, and per hosting DataMiner Agent there can be at most 500 open suggestion events related to behavioral anomaly detection.
  - Prior to DataMiner 10.2.11/10.3.0, suggestion events are created for all anomalous behavioral changes that do not have alarm monitoring enabled.
