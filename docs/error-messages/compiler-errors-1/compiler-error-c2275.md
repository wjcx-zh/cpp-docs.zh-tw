---
title: 編譯器錯誤 C2275 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2275
dev_langs:
- C++
helpviewer_keywords:
- C2275
ms.assetid: c1eafa71-48de-46e0-82f3-b575538ef205
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 45e5948be0544b0fd6854206aa1aeb9c2c23fee1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33173427"
---
# <a name="compiler-error-c2275"></a>編譯器錯誤 C2275
'identifier': 不合法使用這個型別做為運算式  
  
 運算式使用`->`運算子搭配`typedef`識別項。  
  
 下列範例會產生 C2275:  
  
```  
// C2275.cpp  
typedef struct S {  
    int mem;  
} *S_t;  
void func1( int *parm );  
void func2() {  
    func1( &S_t->mem );   // C2275, S_t is a typedef  
}  
```