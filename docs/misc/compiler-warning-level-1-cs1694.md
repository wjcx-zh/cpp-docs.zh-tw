---
title: "編譯器警告 (層級 1) CS1694 | Microsoft Docs"
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
  - "CS1694"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1694"
ms.assetid: 9cb6b5d4-36a0-4b07-9690-14b5105da44b
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS1694
針對前置處理器指示詞所指定的檔名無效。 檔名太長或無效。  
  
 使用 `#pragma checksum` 前置處理器指示詞時，會發生這個警告。 指定的檔名超過 256 個字元。 若要解決這個警告，請使用較短的檔名。  
  
## 範例  
 下列範例會產生 CS1694。  
  
```  
// cs1694.cs #pragma checksum "MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890.txt" {00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F}   // CS1694 class MyClass {}  
```