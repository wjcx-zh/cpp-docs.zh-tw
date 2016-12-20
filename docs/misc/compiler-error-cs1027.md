---
title: "編譯器錯誤 CS1027 | Microsoft Docs"
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
  - "CS1027"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1027"
ms.assetid: a6657f0f-5664-47a5-95cf-803f5a0e0c90
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1027
必須是 \#endif 指示詞  
  
 找不到所指定 `#if` 指示詞的對應 `#endif` [前置處理器指示詞](../Topic/C%23%20Preprocessor%20Directives.md)。 或者，`#if` 區塊內沒有對應 `#region` 指示詞時，編譯器可能發現 `#endregion` 指示詞。  
  
 下列範例會產生 CS1027：  
  
```  
// CS1027.cs #if true   // CS1027, uncomment next line to resolve // #endif namespace x { public class clx { public static void Main() { } } }  
```