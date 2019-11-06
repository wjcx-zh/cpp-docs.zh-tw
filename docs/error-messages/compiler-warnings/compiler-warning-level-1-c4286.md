---
title: 編譯器警告（層級1） C4286
ms.date: 11/04/2016
f1_keywords:
- C4286
helpviewer_keywords:
- C4286
ms.assetid: 93eadd6c-6f36-413b-ba91-c9aa2314685a
ms.openlocfilehash: ed2e6c10e35e53c6a67de9fecfce5da5ae429b93
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626675"
---
# <a name="compiler-warning-level-1-c4286"></a>編譯器警告（層級1） C4286

' type1 '：由基底類別（' type2 '）攔截，行號

指定的例外狀況類型是由先前的處理常式所處理。 第二個 catch 的型別衍生自第一個的型別。 基類的例外狀況會攔截衍生類別的例外狀況。

## <a name="example"></a>範例

```cpp
//C4286.cpp
// compile with: /W1
#include <eh.h>
class C {};
class D : public  C {};
int main()
{
    try
    {
        throw "ooops!";
    }
    catch( C ) {}
    catch( D ) {}  // warning C4286, D is derived from C
}
```