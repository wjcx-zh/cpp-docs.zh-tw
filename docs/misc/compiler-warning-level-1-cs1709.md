---
title: "編譯器警告 (層級 1) CS1709 | Microsoft Docs"
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
  - "CS1709"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1709"
ms.assetid: e2bb1d30-4f30-4e10-82da-df1d3418454c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS1709
對前置處理器指示詞指定的檔名是空的  
  
 您已指定包含檔名的前置處理器指示詞，但該檔案是空的。 若要解決這個警告，請將所需的內容放入檔案。  
  
## 範例  
 下列範例會產生 CS1709。  
  
```  
// CS1709.cs class Test { static void Main() { #pragma checksum "" "{406EA660-64CF-4C82-B6F0-42D48172A799}" ""  // CS1709 } }  
```