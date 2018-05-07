---
title: 編譯器錯誤 C2694 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2694
dev_langs:
- C++
helpviewer_keywords:
- C2694
ms.assetid: 8dc2cec2-67ae-4e16-8c0c-374425aca8bc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1578b6d7c55272c4b798d0222a1da37f5a749ecc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2694"></a>編譯器錯誤 C2694
'override': 覆寫虛擬函式具有較不嚴格的例外狀況規格比基底類別虛擬成員函式 'base'  
  
 虛擬函式已遭覆寫，但在[/Za](../../build/reference/za-ze-disable-language-extensions.md)、 覆寫函式具有較不嚴格[例外狀況規格](../../cpp/exception-specifications-throw-cpp.md)。  
  
 下列範例會產生 C2694:  
  
```  
// C2694.cpp  
// compile with: /Za /c  
class MyBase {  
public:  
   virtual void f(void) throw(int) {  
   }  
};  
  
class Derived : public MyBase {  
public:  
   void f(void) throw(...) {}   // C2694  
   void f2(void) throw(int) {}   // OK  
};  
```