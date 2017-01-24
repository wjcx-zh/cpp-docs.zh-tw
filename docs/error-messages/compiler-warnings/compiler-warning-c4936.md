---
title: "編譯器警告 C4936 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4936"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4936"
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 C4936
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

以 \/clr 或 \/clr:pure 編譯時才支援這個 \_\_declspec  
  
 已使用 `__declspec` 修飾詞，但該 `__declspec` 修飾詞僅有在以 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 選項之一來編譯時才有效。  
  
 如需詳細資訊，請參閱 [appdomain](../../cpp/appdomain.md) 和[處理序](../../cpp/process.md)。  
  
 C4936 總是發出錯誤。  您可以使用 [warning](../../preprocessor/warning.md) pragma 來停用 C4936。  
  
 下列範例會產生 C4936：  
  
```  
// C4936.cpp // compile with: /c // #pragma warning (disable : 4936) __declspec(process) int i;   // C4936 __declspec(appdomain) int j;   // C4936  
```