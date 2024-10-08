---
uid: DIS_2.27
---

# DIS 2.27

## New features

### IDE

#### Version editor \[ID 25967\]

When editing a protocol XML file, you can now click *Version editor* in the file tab header to turn the XML editor into a dedicated protocol version editor. This editor will allow you to manage the information in the Protocol.Version and Protocol.VersionHistory elements in a more user-friendly way.

The editor contains the following main tabs:

| Tab | Description |
|-----|-------------|
| Current version | In this tab, you can specify the general properties of the current (minor) version (ID, author, date, etc.) as well as a list of all features, changes and fixes in this version. |
| Current range | In this tab, you can find an overview of all versions in the current range. Clicking a version number will allow you to edit the information stored for that particular version. |
| All versions | In this tab, you can find an overview of all versions of the current protocol. In the tree structure on the left, you can add and delete branches representing system versions, major versions and minor versions, and in the edit pane on the right, you can edit the properties of the version selected on the left. |

#### New 'Delete QAction' command in shortcut menu of QAction elements \[ID 26007\]

When you open a Protocol.QActions.QAction element’s shortcut menu when editing a protocol XML file, you can now select *Delete QAction*. This will delete the entire QAction element as well as the associated C# project.

> [!NOTE]
> This delete action cannot be undone as it will also remove all associated C# project files stored on disk.

### Validator

#### New checks and error messages \[ID 24138\]

The following checks and error messages have been added.

| ID     | Check                | Error message                                                     |
|--------|----------------------|-------------------------------------------------------------------|
| 1.24.1 | EndlessLoop          | Endless loop detected. Involved items '{involvedItems}'           |
| 1.24.2 | PotentialEndlessLoop | Potential endless loop detected. Involved items '{involvedItems}' |

### XML Schema

#### Protocol Schema: Miscellaneous updates \[ID 25922\]\[ID 25923\]\[ID 25962\]

The Protocol XML schema has been updated.

##### New element

- Protocol.Params.Param.Database.IndexingOptions

##### New element value

- Protocol.Params.Param.Database.Partition can now be set to “infinite”

##### Attributes made mandatory

- Protocol.PortSettings@name
- Protocol.Ports.PortSettings@name

##### Restricted ID range

- Allowed range of Protocol.ParameterGroups.Group@id: 1 to 100,000

#### UOM Schema: New units added \[ID 25941\]

The following units have been added to the UOM Schema:

- Files/s (Files per second)
- dBuW (Decibel microwatt)
- L/h (Liter per hour)
- L/min (Liter per minute)
- Logins (Logins)
- Logins/h (Logins per hour)
- Logins/min (Logins per minute)
- Logins/s (Logins per second)

## Changes

### Fixes

#### Validator: Checking the Trigger.On@id attribute would fail when set to 'each' \[ID 25872\]

Up to now, checking the Trigger.On@id attribute would fail when it was set to “each”.

#### Validator: Checking the TreeControl.ExtraTabs.Tag@parameter attribute would result in false positives \[ID 25873\]

Up to now, checking the TreeControl.ExtraTabs.Tab@parameter attribute would result in false positives when the TreeControl.ExtraTabs.Tab@type attribute was set to “relation” or “summary”.

#### IDE - MIB browser: When multiple MIB modules defined the same OID path only one of the nodes would be added to the tree \[ID 25900\]

Up to now, when multiple MIB modules defined the same OID path, but each with a different name, only one of the nodes would be added to the tree.

From now on, all nodes will be displayed in the tree, even those sharing the same OID. Moreover, duplicate OIDs will now be indicated with a special warning icon.

#### Class Library: Deserialization would fail when 'System.' classes were used \[ID 25933\]

In some cases, collection interface deserialization could fail if some of the classes were “System.” classes located in System.dll.

Deserialization now supports classes located in both System.Core.dll and System.dll.

#### Validator: Problem with clear response routine check \[ID 25989\]

Up to now, the clear response routine check would not take into account that triggers can use the “each” keyword and that one action can clear multiple responses by providing a semicolon-separated list of response IDs.

#### IDE: Problem with absolute paths to code analysis rule set files \[ID 26035\]

Up to now, the C# projects generated by DIS would contain an absolute path to the code analysis rule set files that included a unique ID that changed each time DIS was upgraded.

Since the introduction of solution-based protocols in DIS 2.26, specifying an absolute path to the code analysis rule set files would cause DIS to no longer be able to locate those files. From now on, every protocol solution will have its own collection of rule set files.

#### Validator: Checking the QAction@triggers attribute could result in a false positive \[ID 26036\]

Checking the QAction@triggers attribute could result in a false positive when the attribute contained an ID of a general parameter (i.e. an ID greater than 65,000).
