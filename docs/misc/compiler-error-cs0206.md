---
title: "編譯器錯誤 CS0206 | Microsoft Docs"
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
  - "CS0206"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0206"
ms.assetid: d2f9838a-d8ae-4342-b8bd-fa5745619a26
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0206
可能無法將屬性或索引子當做 out 或 ref 參數傳遞  
  
 [屬性](../Topic/Properties%20\(C%23%20Programming%20Guide\).md)不可傳遞為 [ref](../Topic/ref%20\(C%23%20Reference\).md) 或 [out](../Topic/out%20\(C%23%20Reference\).md) 參數。 如需詳細資訊，請參閱[傳遞參數](../Topic/Passing%20Parameters%20\(C%23%20Programming%20Guide\).md)。  
  
## 範例  
 下列範例會產生 CS0206：  
  
```  
// CS0206.cs public class MyClass { public static int P { get { return 0; } set { } } public static void MyMeth(ref int i) // public static void MyMeth(int i) { } public static void Main() { MyMeth(ref P);   // CS0206 // try the following line instead // MyMeth(P);   // CS0206 } }  
```