---
title: 編譯器錯誤 C3736 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3736
dev_langs:
- C++
helpviewer_keywords:
- C3736
ms.assetid: 579b773c-41e7-40ea-8382-2e3ce2667f4c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e4268e8f01d01147351cb1e9810c05eae0ef215
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274687"
---
# <a name="compiler-error-c3736"></a>編譯器錯誤 C3736
'event': 必須是方法，或如果是 managed 事件，您可以選擇的資料成員  
  
 原生和 COM 事件必須是方法。 .NET 事件也可以是資料成員。  
  
 下列範例會產生 C3736:  
  
```  
// C3736.cpp  
struct A {  
   __event int e();  
};  
  
struct B {  
   int f;   // C3736  
   // The following line resolves the error.  
   // int f();  
   B(A* a) {  
      __hook(&A::e, a, &B::f);  
   }  
};  
  
int main() {  
}  
```