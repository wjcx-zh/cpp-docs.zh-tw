---
title: "編譯器錯誤 CS0738 | Microsoft Docs"
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
  - "CS0738"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0738"
ms.assetid: 01ce94ee-2435-4326-befc-2b020c441a4f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0738
'type name' 未實作介面成員 'member name'。 'method name' 無法實作 'interface member'，因為它沒有符合的傳回類型 'type name'。  
  
 類別中實作方法的傳回值必須符合其所實作之介面成員的傳回值。  
  
### 更正這個錯誤  
  
1.  請變更方法的傳回類型，使其符合介面成員的傳回類型。  
  
## 範例  
 因為類別方法傳回 `void`，而且同名的介面成員傳回 `int`，所以下列程式碼會產生 CS0738：  
  
```  
using System; interface ITest { int TestMethod(); } public class Test: ITest { public void TestMethod() { } // CS0738 // Try the following line instead. // public int TestMethod(); }  
```  
  
## 請參閱  
 [介面](../Topic/Interfaces%20\(C%23%20Programming%20Guide\).md)