---
title: "編譯器錯誤 CS0708 | Microsoft Docs"
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
  - "CS0708"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0708"
ms.assetid: 19e1907f-b78c-4c8b-b78c-eedfd57115f2
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0708
'field': 不能在靜態類別中宣告執行個體成員  
  
 如果您在已宣告靜態的類別中宣告非靜態的成員，就會發生此錯誤。 不可能建立靜態類別的執行個體，因此執行個體變數沒有意義。**static** 關鍵字應該套用至靜態類別的所有成員。  
  
 下列範例會產生 CS0708：  
  
```  
// CS0708.cs // compile with: /target:library public static class C { int i;  // CS0708 static int j;  // OK }  
```