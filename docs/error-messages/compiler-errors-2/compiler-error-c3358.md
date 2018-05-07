---
title: 編譯器錯誤 C3358 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3358
dev_langs:
- C++
helpviewer_keywords:
- C3358
ms.assetid: 180b93df-e78f-441a-91fb-1594c681f7f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92e72d3dabdb67ee595d9747ad5fa1f9f3909ce9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3358"></a>編譯器錯誤 C3358
'symbol': 找不到符號  
  
 找不到必要的符號。  
  
 下列範例會產生 C3358：  
  
```  
// C3358.cpp  
#define __ATLEVENT_H__ 1   // remove this line to resolve the error  
#define _ATL_ATTRIBUTES 1  
#include "atlbase.h"  
#include "atlcom.h"  
  
[event_receiver(com)]  
struct A   // C3358  
{  
   void func();  
};  
  
int main()  
{  
}  
```