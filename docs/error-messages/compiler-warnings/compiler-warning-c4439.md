---
title: "編譯器警告 C4439 | Microsoft Docs"
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
  - "C4439"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4439"
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 C4439
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 簽章中有 Managed 型別的函式定義必須有 \_\_clrcall 呼叫慣例  
  
 編譯器以隱含方式用 [\_\_clrcall](../../cpp/clrcall.md) 取代了呼叫慣例。  若要解除這項警告，請移除 `__cdecl` 或 `__stdcall` 呼叫慣例。  
  
 C4439 永遠視同錯誤。  您可以使用 `#pragma warning` 或 **\/wd** 關閉這個警告。如需詳細資訊，請參閱 [warning](../../preprocessor/warning.md) 或 [\/w、\/Wn、\/WX、\/Wall、\/wln、\/wdn、\/wen、\/won \(警告層級\)](../../build/reference/compiler-option-warning-level.md)。  
  
## 範例  
 下列範例會產生 C4439。  
  
```  
// C4439.cpp  
// compile with: /clr  
void __stdcall f( System::String^ arg ) {}   // C4439  
void __clrcall f2( System::String^ arg ) {}   // OK  
void f3( System::String^ arg ) {}   // OK  
```