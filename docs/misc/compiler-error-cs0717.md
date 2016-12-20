---
title: "編譯器錯誤 CS0717 | Microsoft Docs"
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
  - "CS0717"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0717"
ms.assetid: 1976e82a-d048-4f13-a95a-a7f4e3cd7038
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0717
'static class': 靜態類別不能當做條件約束使用  
  
 靜態類別無法擴充，因為它們只包含靜態成員，而未包含執行個體成員。 因為它們無法擴充，這使得它們無法用來作為類型參數和條件約束，因為沒有任何類型可以是靜態類別的特製化。  
  
## 範例  
 下列範例會產生 CS0717：  
  
```  
// CS0717.cs public static class SC { public static void F() { } } public class G<T> where T : SC  // CS0717 { public static void Main() { } }  
```