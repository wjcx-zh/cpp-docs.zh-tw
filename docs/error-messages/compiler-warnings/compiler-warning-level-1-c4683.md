---
title: "編譯器警告 (層級 1) C4683 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4683"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4683"
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4683
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**'**   
 ***function* ': 事件來源有 'out' 參數; 當攔截多個事件處理常式時發出警告**  
  
 如果有一個以上的事件接收 \(Event Sink\) 接聽 \(Listen\) COM 事件來源，out 參數的值可能會被忽略。  
  
 請注意，下列情況將會發生記憶體遺漏 \(Memory Leak\)：  
  
1.  如果方法擁有內部配置的 out 參數，例如，BSTR \*。  
  
2.  如果該事件擁有一個以上的處理常式 \(即多點傳送事件\)  
  
 造成遺漏的原因，是因為該 out 參數會由多個處理常式設定，但只由最後一個處理常式傳回至呼叫位置。  
  
 下列範例會產生 C4683：  
  
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