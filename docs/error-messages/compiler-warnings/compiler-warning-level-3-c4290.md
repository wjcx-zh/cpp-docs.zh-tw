---
title: 編譯器警告 （層級 3） C4290 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4290
dev_langs:
- C++
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f03d35e1a3756979d8936647255e2b65afef56d9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4290"></a>編譯器警告 (層級 3) C4290
忽略除了用來表示函式的 c + + 例外狀況規格不 __declspec （nothrow）  
  
 使用例外狀況規格，其中 Visual c + + 接受，但未實作宣告的函式。 發生例外狀況規格，在編譯期間會忽略可能需要重新編譯程式碼及連結要重複使用在未來版本支援例外狀況規格。  
  
 如需詳細資訊，請參閱[例外狀況規格 (throw)](../../cpp/exception-specifications-throw-cpp.md) 。  
  
 您可以使用，以避免這個警告[警告](../../preprocessor/warning.md)pragma:  
  
```  
#pragma warning( disable : 4290 )  
```  
  
 下列程式碼範例會產生 C4290:  
  
```  
// C4290.cpp  
// compile with: /EHs /W3 /c  
void f1(void) throw(int) {}   // C4290  
  
// OK  
void f2(void) throw() {}  
void f3(void) throw(...) {}  
```