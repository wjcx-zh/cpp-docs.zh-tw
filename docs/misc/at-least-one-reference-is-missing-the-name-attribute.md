---
title: "At least one reference is missing the &#39;Name&#39; attribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.refmissingname"
ms.assetid: 0703dc20-9cdd-4632-93a0-57a4ccea2fce
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one reference is missing the &#39;Name&#39; attribute
每個參考都必須具有相關的 **Name** 屬性，如下所示：  
  
```  
<Reference  
   Name = "System.XML"  
   AssemblyName = "System.Xml"  
/>  
```  
  
 這個錯誤表示至少有一個參考找不到 **Name** 屬性。  
  
 最可能導致這個錯誤的原因是以手動方式編輯專案檔。  
  
 **若要更正這個錯誤**  
  
-   再次加入參考。  
  
     任何受影響的參考都不會被加入專案中。  
  
## 請參閱  
 [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/zh-tw/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [管理專案中的參考](../Topic/Managing%20references%20in%20a%20project.md)