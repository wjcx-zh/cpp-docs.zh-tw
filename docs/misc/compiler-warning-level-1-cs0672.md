---
title: "編譯器警告 (層級 1) CS0672 | Microsoft Docs"
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
  - "CS0672"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0672"
ms.assetid: 140a8708-97d0-444b-980b-62e74328cafb
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS0672
成員 'member1' 會覆寫過時成員 'member2'。 將 Obsolete 屬性加入 'member1'  
  
 編譯器發現方法的 `override` 標記為 `obsolete`。 不過，覆寫方法本身未標記為過時。 覆寫方法仍會產生 [CS0612](../misc/compiler-warning-level-1-cs0612.md) \(呼叫時\)。  
  
 請檢閱方法宣告，並明確表示方法 \(和其所有覆寫\) 是否應該標記為 `obsolete`。  
  
 下列範例會產生 CS0672：  
  
```  
// CS0672.cs // compile with: /W:1 class MyClass { [System.Obsolete] public virtual void ObsoleteMethod() { } } class MyClass2 : MyClass { public override void ObsoleteMethod()   // CS0672 { } } class MainClass { static public void Main() { } }  
```