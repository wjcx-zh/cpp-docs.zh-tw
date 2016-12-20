---
title: "編譯器錯誤 CS0714 | Microsoft Docs"
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
  - "CS0714"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0714"
ms.assetid: fbb5dc55-645c-4980-bf4b-3c2f84a3c6cd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0714
'靜態類型': 靜態類別不能實作介面  
  
 介面可以定義物件上的非靜態方法，因此可能不是由靜態類別實作。 若要解決這個錯誤，請確定您的類別未嘗試實作任何介面。  
  
## 範例  
 下列範例會產生 CS0714：  
  
```  
// CS0714.cs interface I { } public static class C : I  // CS0714 { public static void Main() { } }  
```