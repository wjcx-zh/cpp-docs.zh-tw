---
title: "編譯器錯誤 CS1109 | Microsoft Docs"
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
  - "CS1109"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1109"
ms.assetid: bebe56b8-3831-4ebb-a49e-e0364b4c11a7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1109
擴充方法必須定義在最上層靜態類別上，'name' 為巢狀類別。  
  
 擴充方法不能定義在巢狀類別中。  
  
## 範例  
 下列範例會產生 CS1109，因為類別 `Extension` 巢狀於類別 `Out` 內：  
  
```  
// cs1109.cs public class Test { } static class Out { static class Extension { static void ExtMethod(this Test c) // CS1109 { } } }  
```  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(C%23%20Programming%20Guide\).md)