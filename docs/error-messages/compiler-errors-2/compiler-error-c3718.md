---
title: 編譯器錯誤 C3718 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3718
dev_langs:
- C++
helpviewer_keywords:
- C3718
ms.assetid: 346b5205-c44d-49d3-b66a-96417d3d6986
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7116ea8b17d4e342079fe5590464699757e96de
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33264203"
---
# <a name="compiler-error-c3718"></a>編譯器錯誤 C3718
只接收類別成員函式的內容中呼叫 'event'  
  
 `event`只可以從接收的類別呼叫。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3718:  
  
```  
// C3718.cpp  
#define _ATL_ATTRIBUTES 1  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module(name="test")];  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface I  
{  
    HRESULT f();  
};  
  
[event_source(com), coclass, uuid("00000000-0000-0000-0000-000000000002")]  
struct E  
{  
    __event __interface I;  
};  
  
[event_receiver(com)]  
struct R  
{  
    void b()  
    {  
        printf_s("B::bar()\n");   
    }  
  
    void HookAndRun(E* pE)  
    {  
        __hook(&I::f, pE->GetUnknown(), &R::b);  
        __raise pE->f();  
    }  
};  
  
int main()  
{  
    CComObject<E>* pE;  
    CComObject<E>::CreateInstance(&pE);  
  
    __hook(&I::f, pE->GetUnknown(), &R::b, &r);   // C3718  
    __raise pE->f();  
    // try the following lines instead  
    // R r;  
    // r.HookAndRun(pE);  
}  
```