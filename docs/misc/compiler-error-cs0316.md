---
title: "編譯器錯誤 CS0316 | Microsoft Docs"
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
  - "CS0316"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0316"
ms.assetid: 8b70abbe-dd4f-473f-8dfe-f8309abef276
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0316
參數名稱 'name' 與自動產生的參數名稱相衝突。  
  
 保留字不能當做參數名稱使用。 在下列範例中，`value` 是預設屬性或索引子存取子內容中的保留字。  
  
### 更正這個錯誤  
  
1.  變更參數名稱。  
  
## 範例  
 下列程式碼會產生 CS0316：  
  
```  
// cs0316.cs // Compile with: /target:library public class Test { public int this[int value] // CS0316 { get { return 1; } set { } } }  
```  
  
## 請參閱  
 [索引子](../Topic/Indexers%20\(C%23%20Programming%20Guide\).md)   
 [C\# 關鍵字](../Topic/C%23%20Keywords.md)