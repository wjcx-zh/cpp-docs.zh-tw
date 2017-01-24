---
title: "編譯器錯誤 CS0644 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0644"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0644"
ms.assetid: 835f3ee2-f897-4ba2-ad13-af629a9ab7fe
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0644
'class1' 不可衍生自特殊類別 'class2'  
  
 類別無法明確繼承自下列任何基底類別：  
  
-   **System.Enum**  
  
-   **System.ValueType**  
  
-   **System.Delegate**  
  
-   **System.Array**  
  
 編譯器使用這些類別作為隱含基底類別。 例如，**System.ValueType** 是結構的隱含基底類別。  
  
 下列範例會產生 CS0644：  
  
```  
// CS0644.cs class MyClass : System.ValueType   // CS0644 { }  
```