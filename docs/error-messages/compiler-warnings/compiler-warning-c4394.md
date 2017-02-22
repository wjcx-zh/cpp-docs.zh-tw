---
title: "編譯器警告 C4394 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4394"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4394"
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 編譯器警告 C4394
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : per\-appdomain 符號不可用 \_\_declspec\(dllexport\) 標記  
  
 用 [appdomain](../../cpp/appdomain.md) `__declspec` 修飾詞標記的函式是編譯為 MSIL \(不是原生\)，而且匯出表格 \([export](../../windows/export.md) `__declspec` 修飾詞\) 也不能支援 Managed 函式。  
  
 您可以宣告 Managed 函式具有公用的存取範圍。  如需詳細資訊，請參閱 [類型可視性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) 和 [成員可視性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility)。  
  
 C4394 永遠視同錯誤。您可以使用 `#pragma warning` 或 **\/wd** 關閉這個警告。如需詳細資訊，請參閱 [warning](../../preprocessor/warning.md) 或 [\/w、\/Wn、\/WX、\/Wall、\/wln、\/wdn、\/wen、\/won \(警告層級\)](../../build/reference/compiler-option-warning-level.md)。  
  
## 範例  
 下列範例會產生 C4394。  
  
```  
// C4394.cpp  
// compile with: /clr /c  
__declspec(dllexport) __declspec(appdomain) int g1 = 0;   // C4394  
__declspec(dllexport) int g2 = 0;   // OK  
```