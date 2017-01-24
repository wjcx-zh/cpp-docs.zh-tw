---
title: "編譯器錯誤 CS0271 | Microsoft Docs"
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
  - "CS0271"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0271"
ms.assetid: eadc9fb5-7770-4ec4-94f6-3c7cf37eec06
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0271
這個內容中不能使用屬性或索引子 'property\/indexer'，因為無法存取 get 存取子  
  
 當您嘗試存取無法存取的 `get` 存取子時，就會發生這個錯誤。 若要解決此錯誤，請增加存取子的存取範圍，或變更呼叫的位置。 如需詳細資訊，請參閱[存取子的存取範圍](../Topic/Restricting%20Accessor%20Accessibility%20\(C%23%20Programming%20Guide\).md)和[屬性](../Topic/Properties%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0271：  
  
```  
// CS0271.cs public class MyClass { public int Property { private get { return 0; } set { } } public int Property2 { get { return 0; } set { } } } public class Test { public static void Main(string[] args) { MyClass c = new MyClass(); int a = c.Property;   // CS0271 int b = c.Property2;   // OK } }  
```