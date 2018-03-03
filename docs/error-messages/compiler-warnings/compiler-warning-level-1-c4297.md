---
title: "編譯器警告 （層級 1） C4297 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4297
dev_langs:
- C++
helpviewer_keywords:
- C4297
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9253ae709109927e69940d5023b542dfb543c6de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4297"></a>編譯器警告 (層級 1) C4297
'function' : 函式預設並不會擲回例外狀況，但卻擲回例外狀況  
  
 函式宣告包含 （可能隱含）`noexcept`規範、 空白`throw`例外狀況規範或[__declspec （nothrow)](../../cpp/nothrow-cpp.md)屬性，並且定義包含一或多個[擲回](../../cpp/try-throw-and-catch-statements-cpp.md)陳述式。 若要解決 C4297，請勿嘗試在宣告 `__declspec(nothrow)`、`noexcept(true)` 或 `throw()` 的函式中擲回例外狀況。 或者，移除 `noexcept`、`throw()` 或 `__declspec(nothrow)` 規格。  
  
 根據預設，編譯器會為使用者定義的解構函式和取消配置函式和編譯器所產生的特殊成員函式產生隱含 `noexcept(true)` 規範。 這會符合 ISO C++11 標準。 若要防止產生隱含 noexcept 規範，並還原編譯器的 Visual Studio 2013 的非標準行為，請使用**/zc: implicitnoexcept-**編譯器選項。 如需詳細資訊，請參閱[/zc: implicitnoexcept （隱含的例外狀況規範）](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md)。  
  
 如需例外狀況規格的詳細資訊，請參閱[例外狀況規格 (throw)](../../cpp/exception-specifications-throw-cpp.md)。 此外，請參閱[/EH （例外狀況處理模型）](../../build/reference/eh-exception-handling-model.md)如需有關如何修改例外狀況處理行為，在編譯時間資訊。  
  
 這個警告也會產生 __declspec ([dllexport](../../cpp/dllexport-dllimport.md)) 函式標記為 extern"C"，即使它們是 c + + 函式。  
  
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