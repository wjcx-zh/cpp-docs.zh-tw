---
title: "編譯器警告 （層級 1） C4683 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4683
dev_langs: C++
helpviewer_keywords: C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e0a8ca498a3c95a1b37229f6ac973cf74a8e28ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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