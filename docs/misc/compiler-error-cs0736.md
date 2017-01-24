---
title: "編譯器錯誤 CS0736 | Microsoft Docs"
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
  - "CS0736"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0736"
ms.assetid: 06b14feb-81d5-495f-ab2d-6dc3f5e7216f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0736
'type name' 未實作介面成員 'member name'。 'method name' 無法實作介面成員，因為其為靜態。  
  
 靜態方法隱含或明確地宣告為介面成員的實作時，會產生這個錯誤。  
  
### 更正這個錯誤  
  
-   從方法宣告中移除[靜態](../Topic/static%20\(C%23%20Reference\).md)修飾詞。  
  
-   變更介面方法的名稱。  
  
-   重新定義包含類型，讓它不是繼承自介面。  
  
## 範例  
 下列程式碼會產生 CS0736，因為 `Program.testMethod` 宣告為靜態：  
  
```  
// cs0736.cs namespace CS0736 { interface ITest { int testMethod(int x); } class Program : ITest // CS0736 { public static int testMethod(int x) { return 0; } // Try the following line instead. // public int testMethod(int x) { return 0; } public static void Main() { } } }  
```  
  
## 請參閱  
 [介面](../Topic/Interfaces%20\(C%23%20Programming%20Guide\).md)