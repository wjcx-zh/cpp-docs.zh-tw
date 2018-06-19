---
title: 編譯器錯誤 C3231 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3231
dev_langs:
- C++
helpviewer_keywords:
- C3231
ms.assetid: fe5dc352-e634-45fa-9534-3da176294c98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4925055caac0f3d26922eebf6a043ad51c83efa2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257992"
---
# <a name="compiler-error-c3231"></a>編譯器錯誤 C3231
'arg': 樣板類型引數不能使用泛型型別參數  
  
 樣板會在編譯時期具現化，但泛型會在執行階段具現化。 因此，您無法產生可呼叫樣板的泛型程式碼，因為當泛型類型最後確定時，無法於該執行階段具現化樣板。  
  
 下列範例會產生 C3231:  
  
```  
// C3231.cpp  
// compile with: /clr /LD  
template <class T> class A;  
  
generic <class T>  
ref class C {  
   void f() {  
      A<T> a;   // C3231  
   }  
};  
```