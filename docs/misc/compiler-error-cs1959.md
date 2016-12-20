---
title: "編譯器錯誤 CS1959 | Microsoft Docs"
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
  - "CS1959"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1959"
ms.assetid: 20a31619-3e30-446a-becc-a7f8cfcec66d
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1959
'name' 為類型 'type'。 常數宣告中指定的類型，必須為 sbyte、byte、short、ushort、int、uint、long、ulong、char、float、double、decimal、bool、string、列舉類型或參考類型。  
  
 常數宣告中允許的類型僅限於這則訊息中所述的類型。  
  
### 更正這個錯誤  
  
1.  以允許的類型來宣告常數。  
  
## 範例  
 下列程式碼會產生 CS1959，因為 `null` 不是類型。  
  
```  
// cs1959.cs class Program { static void Test<T>() where T : class { const T x = null; // CS1959 } }  
```  
  
## 請參閱  
 [常數](../Topic/Constants%20\(C%23%20Programming%20Guide\).md)   
 [null](../Topic/null%20\(C%23%20Reference\).md)