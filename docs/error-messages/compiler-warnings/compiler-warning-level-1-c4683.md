---
title: 編譯器警告 （層級 1） C4683 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4683
dev_langs:
- C++
helpviewer_keywords:
- C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 418bf25d565c616d5bc4aaf58361c4f28df298ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4683"></a>編譯器警告 (層級 1) C4683
**'**   
 ***函式*': 事件來源有 'out' 的參數; 當攔截多個事件處理常式時警告**  
  
 如果一個以上的事件接收器用來接聽以 COM 事件來源，可能會忽略為輸出參數的值。  
  
 請注意下列情況會發生記憶體流失：  
  
1.  如果方法具有輸出參數，會在內部配置，例如 BSTR *。  
  
2.  如果事件都有一個以上的處理常式 （是多點傳送的事件）  
  
 找出遺漏的原因是 out 參數會設定由一個以上的處理常式，但只能由最後一個處理常式傳回至呼叫位置。  
  
 下列範例會產生 C4683:  
  
```  
// C4683.cpp  
// compile with: /W1 /LD  
#define _ATL_ATTRIBUTES 1  
#include "atlbase.h"  
#include "atlcom.h"  
  
[ module(name="xx") ];  
  
[ object ]  
__interface I {  
   HRESULT f([out] int* pi);  
   // try the following line instead  
   // HRESULT f(int* pi);  
};  
  
[ coclass, event_source(com) ]  
struct E {  
   __event __interface I;   // C4683  
};  
```