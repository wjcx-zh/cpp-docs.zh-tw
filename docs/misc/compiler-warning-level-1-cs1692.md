---
title: "編譯器警告 (層級 1) CS1692 | Microsoft Docs"
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
  - "CS1692"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1692"
ms.assetid: 1a6d52e1-0ebb-4990-ac0b-36b05a884a19
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS1692
無效的數字  
  
 一些前置處理器指示詞，例如 `#pragma` 和 `#line` 使用數字作為參數。 這些數字之一無效，因為它太大、格式錯誤、包含不合法的字元等等。 若要更正這個錯誤，請更正數字。  
  
## 範例  
 下列範例會產生 CS1692：  
  
```  
// CS1692.cs #pragma warning disable a  // CS1692 // Try this instad: // #pragma warning disable 1691 class A { static void Main() { } }  
```