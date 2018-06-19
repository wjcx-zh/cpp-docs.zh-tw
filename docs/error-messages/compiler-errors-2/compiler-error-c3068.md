---
title: 編譯器錯誤 C3068 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3068
dev_langs:
- C++
helpviewer_keywords:
- C3068
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f378a60c79defed4fb1738515ca5b65b2851056
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256551"
---
# <a name="compiler-error-c3068"></a>編譯器錯誤 C3068
'function': 'naked' 函式不能包含需要的物件會回溯發生 c + + 例外狀況  
  
 編譯器無法執行上的堆疊回溯[naked](../../cpp/naked-cpp.md)函式擲回例外狀況，因為暫存物件建立在函式和 c + + 例外狀況處理 ([/EHsc](../../build/reference/eh-exception-handling-model.md)) 指定。  
  
 若要解決這個錯誤，請執行至少下列其中一種動作：  
  
-   不使用 /EHsc 編譯。  
  
-   不會標示為函式`naked`。  
  
-   Do 在函式中建立暫存物件。  
  
 如果函式會建立暫存物件在堆疊上，如果函式會擲回的例外狀況，而且如果啟用 c + + 例外狀況處理，編譯器將會清除堆疊發生例外狀況。  
  
 當擲回例外狀況、 編譯器產生的程式碼，呼叫的初構和終解但不會出現在 naked 函式時，會執行函式。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3068:  
  
```  
// C3068.cpp  
// compile with: /EHsc  
// processor: x86  
class A {  
public:  
   A(){}  
   ~A(){}  
};  
  
void b(A){}  
  
__declspec(naked) void c() {  
   b(A());   // C3068   
};  
```