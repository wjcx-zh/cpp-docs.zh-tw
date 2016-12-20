---
title: "編譯器錯誤 CS1666 | Microsoft Docs"
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
  - "CS1666"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1666"
ms.assetid: 4d62aa9c-71b9-4c6e-8141-2426d20ac243
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1666
您不能使用包含在 unfixed 運算式中的固定大小緩衝區。 請嘗試使用 fixed 陳述式。  
  
 如果您在包含本身不固定之類別的運算式中使用固定大小的緩衝區，就會發生此錯誤。 執行階段可以自由地四處移動非固定的類別，以最佳化記憶體存取，這可能導致使用固定大小緩衝區時發生錯誤。 若要避免這個錯誤，請在陳述式上使用 `fixed` 關鍵字。  
  
## 範例  
 下列範例會產生 CS1666：  
  
```  
// CS1666.cs // compile with: /unsafe /target:library unsafe struct S { public fixed int buffer[1]; } unsafe class Test { S field = new S(); private bool example1() { return (field.buffer[0] == 0);   // CS1666 error } private bool example2() { // OK fixed (S* p = &field) { return (p->buffer[0] == 0); } } private bool example3() { S local = new S(); return (local.buffer[0] == 0); } }  
```