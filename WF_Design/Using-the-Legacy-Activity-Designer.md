---
title: "Using the Legacy Activity Designer"
ms.custom: na
ms.date: 10/02/2016
ms.prod: .net-framework-4.6
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
manager: erikre
translation.priority.ht: 
  - cs-cz
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pl-pl
  - pt-br
  - ru-ru
  - tr-tr
  - zh-cn
  - zh-tw
---
# Using the Legacy Activity Designer
This topic describes how to use the activity designer in the legacy Windows Workflow Designer. Use the legacy designer when targeting the .NET Framework version 3.5 or the WinFX.  
  
 The Activity Designer enables you to create your own custom activities.  
  
## Creating a Custom Activity  
 Follow these steps to create a custom activity using the Activity Designer:  
  
1.  On the **Project** menu, click **Add Activity**.  
  
2.  Select the **Activity** or **Activity (with code separation)** template.  
  
    1.  Use the **Activity** template to create an activity with the activity definition and the user code in same code file.  
  
    2.  Use the **Activity (with code separation)** template to create an activity with the activity definition expressed as workflow markup and the user code in a separate code file.  
  
3.  Type an activity name or keep the default name, and then click **Add**.  
  
 You can also create a set of custom activities by creating a new project of type **Workflow Activity Library**. For more information about this project type, see [How to: Create a Workflow Activity Library (Legacy)](../WF_Design/How-to--Create-a-Workflow-Activity-Library--Legacy-.md).  
  
## Configuring an Activity  
 While the Activity Designer is active, you can use the property browser to configure the properties listed in the following table.  
  
|Property|Comments|  
|--------------|--------------|  
|**Name**|Name of the activity.|  
|**Base Class**|Base class that the activity derives from. The default base class is [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). In the **Properties** window, click the **Base Class** ellipses **[…]** to select another base class in the [Browse and Select a .NET Type Dialog Box (Legacy)](../WF_Design/Browse-and-Select-a-.NET-Type-Dialog-Box--Legacy-.md).|  
|**Description**|User-defined description of the activity.|  
|**Enabled**|Set to **True** by default to enable activity execution and validation. Set to **False** to disable activity execution and validation. For information about activity execution and validation, see [Developing Workflow Activities](http://go.microsoft.com/fwlink?LinkID=65024).|  
  
## Adding Child Activities  
 You can drag child activities from the Toolbox to the activity that you are designing. You can then configure each child activity using the property browser.  
  
## See Also  
 [Developing Workflow Activities](http://go.microsoft.com/fwlink?LinkID=65024)   
 [Creating Custom Activities](http://go.microsoft.com/fwlink?LinkID=65021)   
 [Legacy Workflow Activities](../WF_Design/Legacy-Workflow-Activities.md)   
 [Custom Activities Samples](http://go.microsoft.com/fwlink?LinkID=65022)   
 [How to: Create a Workflow Activity Library (Legacy)](../WF_Design/How-to--Create-a-Workflow-Activity-Library--Legacy-.md)   
 [Using the Legacy Workflow Designer](../WF_Design/Using-the-Legacy-Workflow-Designer.md)