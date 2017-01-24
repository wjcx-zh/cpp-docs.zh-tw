---
title: "編譯器錯誤 CS0554 | Microsoft Docs"
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
  - "CS0554"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0554"
ms.assetid: 884db4b2-3a69-4434-9a25-526f596e03c8
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0554
'轉換常式': 使用者定義至\/從衍生類別的轉換  
  
 不允許轉換為衍生類別值的使用者定義轉換；您不需要這類運算子。  
  
 如需使用者定義轉換的詳細資訊，請參閱＜C\# 語言規格＞中的第 6 章。  
  
 下列範例會產生 CS0554：  
  
```  
// CS0554.cs namespace x { public class ii { // delete the conversion routine to resolve CS0554 public static implicit operator ii(a aa) // CS0554 { return new ii(); } } public class a : ii { public static void Main() { } } }  
```