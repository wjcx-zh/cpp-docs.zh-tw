---
title: "編譯器錯誤 CS1104 | Microsoft Docs"
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
  - "CS1104"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1104"
ms.assetid: 65bfe85f-8dd1-4aed-bcd1-1f7e0635868c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1104
擴充方法中，參數陣列不可用於 'this' 修飾詞。  
  
 擴充方法的第一個參數不可為參數陣列。  
  
### 更正這個錯誤  
  
1.  請記住，擴充方法定義的第一個參數會指定方法要「擴充」何種類型。 它不是輸入參數。 因此，在此位置使用參數陣列並沒有任何意義。 如果您一定要傳入參數陣列，請將它作為第二個參數。  
  
## 範例  
 下列範例會產生 CS1104：  
  
```  
// cs1104.cs // Compile with: /target:library public static class Extensions { public static void Test<T>(this params T[] tArr) {} // CS1104 }   
```  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(C%23%20Programming%20Guide\).md)   
 [params](../Topic/params%20\(C%23%20Reference\).md)