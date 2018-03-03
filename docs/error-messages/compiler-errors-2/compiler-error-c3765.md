---
title: "編譯器錯誤 C3765 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3765
dev_langs:
- C++
helpviewer_keywords:
- C3765
ms.assetid: feadee7a-fcfb-402c-af2f-0e656f814a13
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5a38aa20c5937bd062db2f2729071e125b135840
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3765"></a>編譯器錯誤 C3765
'event': 無法在 'type' 標記為 event_receiver 的類別/結構中定義事件  
  
 如果類別標示為[event_receiver](../../windows/event-receiver.md)屬性，此類別不能包含[__event](../../cpp/event.md)宣告。  
  
 下列範例會產生 C3765:  
  
```  
// C3765.cpp  
[event_receiver(native)]  
struct ER2 {  
   __event void f();   // C3765  
   __event void b(int);   // C3765  
};  
```