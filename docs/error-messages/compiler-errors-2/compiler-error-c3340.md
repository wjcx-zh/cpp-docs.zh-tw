---
title: 編譯器錯誤 C3340 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3340
dev_langs:
- C++
helpviewer_keywords:
- C3340
ms.assetid: 23b12298-b92a-4717-8380-f165c998cb8a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc5c412f34c12bcfe890e71cdbe59bd6f8ee7a63
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3340"></a>編譯器錯誤 C3340
'interface': 在 coclass 'class' 中，介面不可以同時為 'restricted' 和 'default'  
  
 [受限制](../../windows/restricted.md) 屬性與 [預設](../../windows/default-cpp.md) 屬性互斥。  
  
 下列範例會產生 C3340：  
  
```  
// C3340.cpp  
#include <windows.h>  
[module(name="MyModule")];  
  
[ object, uuid(373a1a4c-469b-11d3-a6b0-00c04f79ae8f) ]  
__interface IMyIface  
{  
   HRESULT f1();  
};  
  
[ coclass, uuid(373a1a4d-469b-11d3-a6b0-00c04f79ae8f),  
default(IMyIface),  
source(IMyIface),restricted(IMyIface) ]  
class CmyClass // C3340  
{  
};  
  
int main()  
{  
}  
```