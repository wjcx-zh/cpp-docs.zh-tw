---
title: "編譯器錯誤 CS0272 | Microsoft Docs"
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
  - "CS0272"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0272"
ms.assetid: 16a9aab6-922a-45a3-a0ef-f32e99f3950f
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0272
這個內容中不能使用屬性或索引子 'property\/indexer'，因為無法存取 set 存取子  
  
 當程式碼無法存取 `set` 存取子時，就會發生這個錯誤。 若要解決此錯誤，請增加存取子的存取範圍，或變更呼叫的位置。 如需詳細資訊，請參閱[限制存取子的存取範圍](../Topic/Restricting%20Accessor%20Accessibility%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS0272：  
  
```  
// CS0272.cs public class MyClass { public int Property { get { return 0; } private set { } } } public class Test { static void Main() { MyClass c = new MyClass(); c.Property = 10;      // CS0272 // To resolve, remove the previous line // or use an appropriate modifier on the set accessor. } }  
```