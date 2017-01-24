---
title: "編譯器警告 (層級 1) CS1633 | Microsoft Docs"
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
  - "CS1633"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1633"
ms.assetid: f31db218-f880-4fc4-ab34-8bcdc49011da
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS1633
無法辨認的 \#pragma 指示詞  
  
 所使用的 pragma 不是 C\# 編譯器支援的其中一個已知 pragma。 若要解決這個錯誤，請只使用支援的 pragma。  
  
 下列範例會產生 CS1633：  
  
```  
// CS1633.cs // compile with: /W:1 #pragma unknown  // CS1633 class C { public static void Main() { } }  
```