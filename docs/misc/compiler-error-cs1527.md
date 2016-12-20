---
title: "編譯器錯誤 CS1527 | Microsoft Docs"
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
  - "CS1527"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1527"
ms.assetid: a0d52130-d6da-41bb-b153-8e96cbb7e316
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1527
無法明確宣告在命名空間中定義的項目為 private、protected 或 protected internal  
  
 命名空間中的類型宣告可以有[公用](../Topic/public%20\(C%23%20Reference\).md)或[內部](../Topic/internal%20\(C%23%20Reference\).md)存取權。 如果未指定任何可存取性，則**內部**是預設值。  
  
 下列範例會產生 CS1527：  
  
```  
// CS1527.cs namespace Sample { private class C1 {};             // CS1527 protected class C2 {};           // CS1527 protected internal class C3 {};  // CS1527 }  
```  
  
 下列範例會產生 CS1527，因為未在程式碼中明確宣告命名空間時，所有類型宣告都是以隱含方式位於全域命名空間內。  
  
```  
//cs1527_2.cs using System; protected class C4{} private struct S1{}  
```  
  
## 請參閱  
 [命名空間](../Topic/Namespaces%20\(C%23%20Programming%20Guide\).md)   
 [全域](../Topic/global%20\(C%23%20Reference\).md)   
 [:: 運算子](../Topic/::%20Operator%20\(C%23%20Reference\).md)   
 [存取範圍定義域](../Topic/Accessibility%20Domain%20\(C%23%20Reference\).md)   
 [存取修飾詞](../Topic/Access%20Modifiers%20\(C%23%20Programming%20Guide\).md)