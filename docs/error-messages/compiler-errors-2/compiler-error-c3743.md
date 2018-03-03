---
title: "編譯器錯誤 C3743 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3743
dev_langs:
- C++
helpviewer_keywords:
- C3743
ms.assetid: 7ca9a76e-7b60-46d1-ab8b-18600cf1a306
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 11f4387a35bcddd919e0ce648f9409291432521f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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