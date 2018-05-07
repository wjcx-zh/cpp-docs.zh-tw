---
title: 編譯器錯誤 C2681 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2681
dev_langs:
- C++
helpviewer_keywords:
- C2681
ms.assetid: eb42da6d-8d2c-43fd-986b-e73e2b004885
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1e35cf6effdbb5aaed5a898bf19a6b42c3df519e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2681"></a>編譯器錯誤 C2681
'type': 無效的運算式型別名稱  
  
 轉型運算子會嘗試將無效的型別轉換。 例如，如果您使用[dynamic_cast](../../cpp/dynamic-cast-operator.md)運算子，將運算式轉換成指標類型，來源運算式必須是指標。  
  
 下列範例會產生 C2681:  
  
```  
// C2681.cpp  
class A { virtual void f(); };  
  
void g(int i) {  
    A* pa;  
    pa = dynamic_cast<A*>(i);  // C2681  
}  
```