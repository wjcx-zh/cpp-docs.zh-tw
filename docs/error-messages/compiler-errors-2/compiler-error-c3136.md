---
title: 編譯器錯誤 C3136 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3136
dev_langs:
- C++
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f892c7f3d1ca7bf2aebf3ecfe7574182b544fd01
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3136"></a>編譯器錯誤 C3136
'interface': COM 介面只可以繼承自其他 COM 介面，不是 COM 介面 'interface'。  
  
 您所套用的介面[介面屬性](../../windows/interface-attributes.md)繼承自不是 COM 介面的介面。 COM 介面最後繼承自`IUnknown`。 加上的介面屬性的任何介面都是 COM 介面。  
  
 下列範例會產生 C3136:  
  
```  
// C3136.cpp  
#include "unknwn.h"  
  
__interface A   // C3136  
// try the following line instead  
// _interface A : IUnknown  
{  
   int a();  
};  
  
[object]  
__interface B : A  
{  
   int aa();  
};  
```