---
title: "&#39;Throw&#39; statement cannot omit operand outside a &#39;Catch&#39; statement or inside a &#39;Finally&#39; statement"
ms.custom: na
ms.date: "10/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: na
ms.topic: "article"
f1_keywords: 
  - "vbc30666"
  - "bc30666"
helpviewer_keywords: 
  - "BC30666"
ms.assetid: a208a6ea-0e36-4bf1-8984-4de1a0e38a2a
caps.latest.revision: 8
ms.author: "billchi"
manager: "douge"
translation.priority.ht: 
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "ru-ru"
  - "zh-cn"
  - "zh-tw"
translation.priority.mt: 
  - "cs-cz"
  - "pl-pl"
  - "pt-br"
  - "tr-tr"
---
# &#39;Throw&#39; statement cannot omit operand outside a &#39;Catch&#39; statement or inside a &#39;Finally&#39; statement
`Throw` statements outside of `Catch` statement must supply the name of an exception object.  
  
 **Error ID:** BC30666  
  
### To correct this error  
  
1.  Specify the name of an exception object derived from `System.Exception`.  
  
2.  Restructure your code so that the `Throw` statement is inside a `Catch` block.  
  
## See Also  
 [Throw Statement](../Topic/Throw%20Statement%20\(Visual%20Basic\).md)   
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [Exception Class in Visual Basic](assetId:///9aac396f-34ca-4afb-8e6c-e523cb690ba9)   
 [Exception and Error Handling in Visual Basic](assetId:///3e351e73-cf23-40ab-8b60-05794160529e)