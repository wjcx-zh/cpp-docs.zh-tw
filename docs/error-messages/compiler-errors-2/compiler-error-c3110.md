---
title: 編譯器錯誤 C3110
ms.date: 11/04/2016
f1_keywords:
- C3110
helpviewer_keywords:
- C3110
ms.assetid: 821dc71f-896e-4b2d-af0e-aa9932934b7b
ms.openlocfilehash: d067fb958f3bb00ef3e62097225881af9ec91dd6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50570465"
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