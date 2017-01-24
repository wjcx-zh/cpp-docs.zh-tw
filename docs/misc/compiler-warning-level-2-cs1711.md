---
title: "編譯器警告 (層級 2) CS1711 | Microsoft Docs"
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
  - "CS1711"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1711"
ms.assetid: 0021275a-43eb-4295-929e-bb3283577a11
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 2) CS1711
'type' 上的 XML 註解有 'parameter' 的 typeparam 標記，但是沒有這個名稱的類型參數  
  
 泛型類型的文件包括名稱錯誤之類型參數的標記。  
  
## 範例  
 下列程式碼會產生警告 CS1711。  
  
```  
// cs1711.cs // compile with: /doc:cs1711.xml // CS1711 expected using System; ///<typeparam name="WrongName">can be an int</typeparam> class CMain { public static void Main() { } }  
```