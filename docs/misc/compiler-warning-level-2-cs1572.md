---
title: "編譯器警告 (層級 2) CS1572 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1572"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1572"
ms.assetid: 24bc8b96-29d2-4201-bc4e-6b9b5a4f5a1d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 2) CS1572
'construct' 上的 XML 註解有 'parameter' 的 param 標記，但是沒有這個名稱的參數  
  
 使用 [\/doc](../Topic/-doc%20\(C%23%20Compiler%20Options\).md) 編譯器選項時，已針對方法沒有的參數指定註解。 請變更傳遞給名稱屬性的值，或移除其中一個註解行。  
  
 下列範例會產生 CS1572：  
  
```  
// CS1572.cs // compile with: /W:2 /doc:x.xml /// <summary>help text</summary> public class MyClass { /// <param name='Int1'>Used to indicate status.</param> /// <param name='Char1'>Used to indicate status.</param> /// <param name='Char2'>???</param> // CS1572 public static void MyMethod(int Int1, char Char1) { } /// <summary>help text</summary> public static void Main () { } }  
```