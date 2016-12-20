---
title: "編譯器錯誤 CS0405 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0405"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0405"
ms.assetid: 0bf51e24-dc6c-438f-a928-b5bfbf35f81a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0405
類型參數 'type parameter' 有重複的條件約束 'constraint'  
  
 泛型宣告上的兩個條件約束完全相同。 若要清除錯誤，請移除重複項目。  
  
 下列範例會產生 CS0405：  
  
```  
// CS0405.cs interface I { } class C<T> where T : I, I  // CS0405.cs { }  
```