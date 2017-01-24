---
title: "編譯器錯誤 CS0737 | Microsoft Docs"
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
  - "CS0737"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0737"
ms.assetid: d2247770-5546-46f2-a01d-8e2ebfcbb859
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0737
'type name' 未實作介面成員 'member name'。 'method name' 無法實作介面成員，因為它不是公用的。  
  
 實作介面成員的方法必須具有公用存取範圍。 所有介面成員都是 `public`。  
  
### 更正這個錯誤  
  
1.  將[公用](../Topic/public%20\(C%23%20Reference\).md)存取修飾詞加入方法中。  
  
## 範例  
 下列程式碼會產生 CS0737：  
  
```  
// cs0737.cs interface ITest { // Default access of private with no modifier. int Return42(); // Try the following line instead. // public int Return42(); } struct Struct1 : ITest // CS0737 { int Return42() { return (42); } } public class Test { public static int Main(string[] args) { Struct1 s1 = new Struct1(); return (1); } }  
```  
  
## 請參閱  
 [介面](../Topic/Interfaces%20\(C%23%20Programming%20Guide\).md)