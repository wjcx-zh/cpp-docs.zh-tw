---
title: "編譯器警告 (層級 3) CS0659 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0659"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0659"
ms.assetid: 63435ee6-c92f-4124-95d4-d8f4e5f0af80
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 3) CS0659
'class' 覆寫了 Object.Equals\(object o\)，但並沒有覆寫 Object.GetHashCode\(\)  
  
 編譯器偵測到 **Equals** 函式的覆寫，但並未偵測到 **GetHashCode** 的覆寫。**Equals** 的覆寫表示您也需要覆寫 **GetHashCode**。  
  
 如需詳細資訊，請參閱  
  
-   <xref:System.Collections.Hashtable>.  
  
-   [等號比較運算子](../Topic/Equality%20Operators.md)  
  
-   [NIB：實作 Equals 方法](http://msdn.microsoft.com/zh-tw/30f28aaf-8b9e-46cd-a746-58a12473af2c)  
  
-   <xref:System.Object.GetHashCode%2A>  
  
 下列範例會產生 CS0659：  
  
```  
// CS0659.cs // compile with: /W:3 /target:library class Test { public override bool Equals(object o) { return true; }   // CS0659 } // OK class Test2 { public override bool Equals(object o) { return true; } public override int GetHashCode() { return 0; } }  
```