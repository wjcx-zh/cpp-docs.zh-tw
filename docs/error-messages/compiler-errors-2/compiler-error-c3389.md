---
title: "編譯器錯誤 C3389 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3389"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3389"
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C3389
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\_\_declspec\(keyword\) 不能配合 \/clr:pure 或 \/clr:safe 使用  
  
 所使用的 [\_\_declspec](../../cpp/declspec.md) 修飾詞隱含處理序專屬狀態。[\/clr:pure](../../build/reference/clr-common-language-runtime-compilation.md) 隱含 per [appdomain](../../cpp/appdomain.md) 狀態。因此，不允許以 `keyword` **\_\_declspec** 修飾詞宣告變數和以 **\/clr:pure** 編譯。  
  
 下列範例會產生 C3389：  
  
```  
// C3389.cpp  
// compile with: /clr:pure /c  
__declspec(dllexport) int g2 = 0;   // C3389  
```