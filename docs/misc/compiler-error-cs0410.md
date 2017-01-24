---
title: "編譯器錯誤 CS0410 | Microsoft Docs"
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
  - "CS0410"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0410"
ms.assetid: a8b11042-9119-465e-abf6-235cbc7b8db5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0410
沒有任何 'method' 的多載具有正確的參數和傳回類型  
  
 如果您嘗試具現化的委派具有包含錯誤參數類型的函式，則會發生這個錯誤。 委派的參數類型必須符合您指派給委派的函式。  
  
## 範例  
 下列範例會產生 CS0410：  
  
```  
// CS0410.cs // compile with: /langversion:ISO-1 class Test { delegate void D(double d ); static void F(int i) { } static void Main() { D d = new D(F);  // CS0410 } }  
```