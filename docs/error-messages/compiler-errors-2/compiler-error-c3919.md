---
title: 編譯器錯誤 C3919 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3919
dev_langs:
- C++
helpviewer_keywords:
- C3919
ms.assetid: 5f8eddda-d751-478b-930d-e18f7191ddfb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c210e85d9f53ae037852e880e12f3015c925642e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270986"
---
# <a name="compiler-error-c3919"></a>編譯器錯誤 C3919
'event_method': 函式必須有類型 'type'  
  
 事件存取子方法宣告不正確。  
  
 如需有關事件的詳細資訊，請參閱[事件](../../windows/event-cpp-component-extensions.md)。  
  
 下列範例會產生 C3919:  
  
```  
// C3919.cpp  
// compile with: /clr /c  
using namespace System;  
delegate void D(String^);  
ref class R {  
   event D^ e {  
      int add(int);   // C3919  
      int remove(int);   // C3919  
  
      void add(D^);   // OK  
      void remove(D^);   // OK  
   }  
};  
```