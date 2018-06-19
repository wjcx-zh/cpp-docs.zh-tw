---
title: 編譯器錯誤 C3743 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3743
dev_langs:
- C++
helpviewer_keywords:
- C3743
ms.assetid: 7ca9a76e-7b60-46d1-ab8b-18600cf1a306
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc9a0bab67bb4fb15627dde42b1d538a0ecce9d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266512"
---
# <a name="compiler-error-c3743"></a>編譯器錯誤 C3743
可以只攔截/取消攔截整個介面當 event_receiver 的 'layout_dependent' 參數為 true 時  
  
 [__Unhook](../../cpp/unhook.md)函式而有所不同，它會使用根據傳遞給的值的參數數目`layout_dependent`中的參數[event_receiver](../../windows/event-receiver.md)類別。  
  
 下列範例會產生 C3743:  
  
```  
// C3743.cpp  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
[module(name="xx")];  
[object] __interface I { HRESULT f(); };  
  
[event_receiver(com, layout_dependent=true), coclass]  
struct R : I {  
        HRESULT f() {  
      return 0;  
   }  
        R() {  
   }  
  
   R(I* a) {  
      __hook(I, a, &R::f);   // C3743  
      // The following line resolves the error.  
      // __hook(I, a);  
   }  
};  
```