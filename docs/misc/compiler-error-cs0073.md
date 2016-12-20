---
title: "編譯器錯誤 CS0073 | Microsoft Docs"
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
  - "CS0073"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0073"
ms.assetid: 579ae534-59ab-4fc5-ad7e-f87639f3f9cd
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0073
add 或 remove 存取子必須具有主體  
  
 [事件](../Topic/event%20\(C%23%20Reference\).md)定義中的**加入**或**移除**關鍵字必須有主體。 如需詳細資訊，請參閱[事件](../Topic/Events%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0073：  
  
```  
// CS0073.cs delegate void del(); class Test { public event del MyEvent { add;   // CS0073 // try the following lines instead // add // { //    MyEvent += value; // } remove { MyEvent -= value; } } public static void Main() { } }  
```