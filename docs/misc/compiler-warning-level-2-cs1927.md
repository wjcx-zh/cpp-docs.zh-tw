---
title: "編譯器警告 (層級 2) CS1927 | Microsoft Docs"
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
  - "CS1927"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1927"
ms.assetid: 32b4e58f-668c-4596-9529-7f3a293ff4ac
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 2) CS1927
因為模組的 \/win32manifest 僅適用於組件，因此將予以忽略。  
  
 win32 資訊清單只會套用至組件層級。 您的模組會進行編譯，但不會有資訊清單。  
  
### 更正這個錯誤  
  
1.  請移除 **\/win32manifest option**。  
  
2.  將程式碼編譯為組件。  
  
## 範例  
 下列範例同時使用 **\/target:module** 和 **\/win32manifest** 編譯器選項進行編譯時會產生 CS1927。  
  
```  
// cs1927.cs // Compile with: /target:module /win32manifest using System; class ManifestWithModule { static int Main() { return 1; } }  
```  
  
## 請參閱  
 [\/win32manifest \(Import a Custom Win32 Manifest File\)](../Topic/-win32manifest%20\(C%23%20Compiler%20Options\).md)   
 [\/target:module \(Create Module to Add to Assembly\)](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md)