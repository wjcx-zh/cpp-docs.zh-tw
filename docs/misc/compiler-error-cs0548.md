---
title: "編譯器錯誤 CS0548 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0548"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0548"
ms.assetid: c4d34da7-0b4a-4312-ac7f-46db100e43c7
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0548
'property': 屬性或索引子至少必須有一個存取子  
  
 一個屬性至少必須有一個存取子 \(get 或 set\) 方法。  
  
 如需詳細資訊，請參閱[使用屬性](../Topic/Using%20Properties%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS0548。  
  
```  
// CS0548.cs // compile with: /target:library public class b { public int MyProp {}   // CS0548 public int MyProp2   // OK { get { return 0; } set {} } }  
```