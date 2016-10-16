---
title: "How to: Migrate a Domain-Specific Language to a New Version"
ms.custom: na
ms.date: 10/03/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6a1ae073-443e-45ca-8bc9-9b944362b449
caps.latest.revision: 14
manager: kamrani
---
# How to: Migrate a Domain-Specific Language to a New Version
You can migrate projects that define and use domain-specific language to Visual Studio 2010 from the version of Domain-Specific Language Tools that was distributed with Visual Studio 2008.  
  
 A migration tool is provided as part of Visual Studio SDK. The tool converts Visual Studio projects and solutions that use or define DSL Tools.  
  
 You must run the migration tool explicitly: it is not launched automatically when you open a solution in Visual Studio. The tool and detailed guidance document can be found at this path:  
  
 **%Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
## Before you Migrate your DSL Projects  
 The migration tool modifies Visual Studio project files (**.csproj**) and solution files (**.sln**).  
  
#### To prepare projects for migration.  
  
-   Make sure the **.csproj** and **.sln** files can be written. If they are under source control, make sure that they are checked out.  
  
-   Make a copy of the folders you intend to migrate.  
  
## Migrating a Collection of Projects  
  
#### To Migrate DSL Projects and Solutions to Visual Studio 2010  
  
1.  Start the DSL Migration Tool.  
  
    -   You can double-click the tool in Windows Explorer (or File Explorer), or start the tool from a command prompt. The tool is in this location:  
  
         **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
2.  Choose a folder that contains solutions and projects that you want to convert.  
  
    -   Enter the path in the box at the top of the tool, or click **Browse**.  
  
     The migration tool displays a tree of projects that define or use DSLs. The tree includes every project that uses the **Microsoft.VisualStudio.Modeling.Sdk** or **TextTemplating** assemblies.  
  
3.  Review the tree of projects, and uncheck projects that you do not want to convert.  
  
    -   Select a project or solution to see a list of changes that the tool will make.  
  
        > [!NOTE]
        >  The checkboxes that appear next to folder names have no effect. You must expand the folders to inspect the projects and solutions.  
  
4.  Convert the projects.  
  
    1.  Click **Convert**.  
  
         Before each project file is converted, a copy of *project***.csproj** is saved as *project***.vs2008.csproj**  
  
         A copy of each *solution***.sln** is saved as *solution***.vs2008.sln**  
  
    2.  Investigate any failed conversions that are reported.  
  
         Failures are reported in the text window. In addition, the tree view shows a red flag on each node that has failed to convert. You can click the node to get more information about that failure.  
  
5.  **Transform All Templates** in solutions containing successfully converted projects.  
  
    1.  Open the solution.  
  
    2.  Click the **Transform All Templates** button in the header of Solution Explorer.  
  
        > [!NOTE]
        >  You can make this step unnecessary. For more information, see [How to Automate Transform All Templates](assetId:///b63cfe20-fe5e-47cc-9506-59b29bca768a).  
  
6.  Update your custom code in the converted projects.  
  
    -   Attempt to build the projects, and investigate any failures.  
  
    -   Test your designer.  
  
## See Also  
 [What's New in Visualization and Modeling SDK](../VS_not_in_toc/What-s-New-in-Visualization-and-Modeling-SDK.md)