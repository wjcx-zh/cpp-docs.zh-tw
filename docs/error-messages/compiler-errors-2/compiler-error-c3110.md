---
title: 編譯器錯誤 C3110 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3110
dev_langs:
- C++
helpviewer_keywords:
- C3110
ms.assetid: 821dc71f-896e-4b2d-af0e-aa9932934b7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81a5ebca8b1ad4fcc93b57ba49bce64a554131a9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077083"
---
# <a name="compiler-error-c3110"></a>編譯器錯誤 C3110

'function_name': 無法多載 COM 介面方法

開頭處會有介面屬性，例如介面：

- [custom](../../windows/custom-cpp.md)

- [dispinterface](../../windows/dispinterface.md)

- [dual](../../windows/dual.md)

- [object](../../windows/object-cpp.md)

無法多載。 例如: 

```
// C3110.cpp
#include <unknwn.h>
[ object, uuid= "4F98A180-EF37-11D1-978D-0000F805D73B" ]
__interface ITestInterface
{
   HRESULT mf1(void);
   HRESULT mf1(BSTR); // C3110
};

int main()
{
}
```