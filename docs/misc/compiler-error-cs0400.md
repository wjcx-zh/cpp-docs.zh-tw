---
title: "編譯器錯誤 CS0400 | Microsoft Docs"
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
  - "CS0400"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0400"
ms.assetid: 58f91f3b-30f4-433b-9a13-0cff258a2630
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0400
在全域命名空間中找不到類型或命名空間名稱 'identifier' \(您是否遺漏了組件參考?\)  
  
 全域命名空間中找不到以全域範圍運算子設定範圍的識別項 \(`::`\)。 您可能遺失了包含識別項的組件參考，或識別項可能是在全域命名空間以外的類別或命名空間中宣告。 如果全域範圍的識別項未宣告或拼字錯誤，也可能會發生這個錯誤。  
  
 若要避免這個錯誤，請找出識別項的宣告、確認正確的拼字，如果宣告位在分開的組件中，請確定您有適當的組件參考。 如果識別項在另一個類型或命名空間中宣告，請在 :: 後面使用完整名稱。 下列範例會產生 CS0400：  
  
```  
// CS0400.cs class C { public static void Main() { // CS0400 - D could not be found // in the global namespace. global::D d = new global::D(); } }  
```