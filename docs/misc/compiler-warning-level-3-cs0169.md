---
title: "編譯器警告 (層級 3) CS0169 | Microsoft Docs"
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
  - "CS0169"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0169"
ms.assetid: 04b0015f-658d-440a-b9ba-831178f1a180
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 3) CS0169
絕不會使用私用欄位 'class member'  
  
 已宣告私用變數但從未參考。 在您宣告類別的私用成員但未使用時，通常會產生這個警告。  
  
 下列範例會產生 CS0169：  
  
```  
// compile with: /W:3 using System; public class ClassX { int i;   // CS0169, i is not used anywhere public static void Main() { } }  
```