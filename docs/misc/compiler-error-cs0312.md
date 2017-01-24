---
title: "編譯器錯誤 CS0312 | Microsoft Docs"
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
  - "CS0312"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0312"
ms.assetid: 552db0ae-2ecf-4beb-9606-bbe58e5708f6
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0312
'type1' 類型不能作為泛型類型或 'name' 方法中的類型參數 'name' 使用。 可為 Null 的類型 'type1' 無法滿足 'type2' 的條件約束。  
  
 可為 Null 的類型會與其不可為 Null 的對應項目不同；它們之間沒有隱含參考轉換或識別轉換存在。 可為 Null 的 boxing 轉換不符合泛型類型條件約束。 在接下來的範例中，第一個類型參數是 `Nullable<int>`，第二個類型參數是 `System.Int32`。  
  
### 更正這個錯誤  
  
1.  請移除條件約束。  
  
2.  在下列範例中，請讓第二個類型引數成為 `int?` 或 `object`。  
  
## 範例  
 下列程式碼會產生 CS0312：  
  
```  
// cs0312.cs class Program { static void MTyVar<T, U>() where T : U { } static int Main() { MTyVar<int?, int>(); // CS0312 return 1; } }  
```  
  
 雖然可為 Null 的類型與不可為 Null 的類型不同，但在可為 Null 與不可為 Null 的值之間允許各種轉換。  
  
## 請參閱  
 [可為 Null 的類型](../Topic/Nullable%20Types%20\(C%23%20Programming%20Guide\).md)