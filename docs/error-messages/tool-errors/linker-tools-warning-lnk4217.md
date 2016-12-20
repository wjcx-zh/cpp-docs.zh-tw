---
title: "連結器工具警告 LNK4217 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4217"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4217"
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具警告 LNK4217
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本機定義的符號 symbol 已匯入函式 function  
  
 符號指定了 [\_\_declspec\(dllimport\)](../../cpp/dllexport-dllimport.md)，即使該符號已經是本機定義。  請移除 `__declspec` 修飾詞 \(Modifier\) 以解決這個警告。  
  
 `symbol` 是定義在影像之內的符號名稱。  `function` 是匯入該符號的函式。  
  
 使用選項 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 進行編譯時，不會出現這個警告。  
  
 如果您嘗試將兩個模組連結在一起，而其實您應該使用第一個模組的匯入程式庫編譯第二個模組，也可能會發生 LNK4217。  
  
```  
// LNK4217.cpp  
// compile with: /LD  
#include "windows.h"  
__declspec(dllexport) void func(unsigned short*) {}  
```  
  
 然後，  
  
```  
// LNK4217b.cpp  
// compile with: /c  
#include "windows.h"  
__declspec(dllexport) void func(unsigned short*) {}  
```  
  
 嘗試連結這兩個模組將產生 LNK4217，請使用第一個範例的匯入程式庫編譯第二個範例，解除這項錯誤。