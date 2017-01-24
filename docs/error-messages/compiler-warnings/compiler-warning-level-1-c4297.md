---
title: "編譯器警告 (層級 1) C4297 | Microsoft Docs"
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
  - "C4297"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4297"
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4297
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 函式預設並不會擲回例外狀況，但卻擲回例外狀況  
  
 函式宣告包含 \(可能是隱含\) `noexcept` 規範、空白 `throw` 例外狀況規範或 [\_\_declspec \(nothrow\)](../../cpp/nothrow-cpp.md) 屬性，並且定義包含一或多個 [throw](../../cpp/try-throw-and-catch-statements-cpp.md) 陳述式。  若要解決 C4297，請勿嘗試在宣告 `__declspec(nothrow)`、`noexcept(true)` 或 `throw()` 的函式中擲回例外狀況。  或者，移除 `noexcept`、`throw()` 或 `__declspec(nothrow)` 規格。  
  
 根據預設，編譯器會為使用者定義的解構函式和取消配置函式和編譯器所產生的特殊成員函式產生隱含 `noexcept(true)` 規範。  這會符合 ISO C\+\+11 標準。  若要防止產生隱含 noexcept 規範，並將編譯器還原為 Visual Studio 2013 的非標準行為，請使用 **\/Zc:implicitNoexcept\-** 編譯器選項。  如需詳細資訊，請參閱 [\/Zc:implicitNoexcept \(隱含的例外狀況規範\)](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md)。  
  
 如需例外狀況規格的詳細資訊，請參閱[例外狀況規格 \(throw\)](../../cpp/exception-specifications-throw-cpp.md)。  此外，請參閱 [\/EH \(例外狀況處理模型\)](../../build/reference/eh-exception-handling-model.md)，以取得如何在編譯時期修改例外狀況處理行為的詳細資訊。  
  
 此警告也會對標示為 extern "C" 的 \_\_declspec\([dllexport](../../cpp/dllexport-dllimport.md)\) 函式產生，即使它們是 C\+\+ 函式。  
  
 下列範例會產生 C4297：  
  
```  
// C4297.cpp  
// compile with: /W1 /LD  
void __declspec(nothrow) f1()   // declared nothrow  
// try the following line instead  
// void f1()  
{  
   throw 1;   // C4297  
}  
```