---
title: "編譯器錯誤 CS1913 | Microsoft Docs"
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
  - "CS1913"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1913"
ms.assetid: 652494b3-9576-4a4c-a9ee-695f86c4a023
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1913
無法初始化成員 'name'。 它不是欄位或屬性。  
  
 物件初始設定式僅能用來初始化可存取的欄位或屬性。  
  
### 更正這個錯誤  
  
1.  初始化一般建構函式或其他初始化方法中的類別成員。  
  
## 範例  
 下列範例會產生 CS1913：  
  
```  
// cs1912.cs class A { public delegate void D(); public event D myEvent; } public class Test { static void Main() { A a = new A() {myEvent = M}; // CS1913 } public void M(){} }  
```  
  
## 請參閱  
 [類別和結構](../Topic/Classes%20and%20Structs%20\(C%23%20Programming%20Guide\).md)