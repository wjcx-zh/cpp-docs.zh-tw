---
title: 編譯器警告 (層級 1) C4286
ms.date: 11/04/2016
f1_keywords:
- C4286
helpviewer_keywords:
- C4286
ms.assetid: 93eadd6c-6f36-413b-ba91-c9aa2314685a
ms.openlocfilehash: be02d330678eaab7f538ed092641f957bdcb01b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207065"
---
# <a name="compiler-warning-level-1-c4286"></a>編譯器警告 (層級 1) C4286

'type1': 由基底類別 ('type2') 行號攔截

指定的例外狀況類型是由前一個處理常式處理。 第二個 catch 的類型被衍生自第一種。 基底類別的例外狀況攔截例外狀況衍生的類別。

## <a name="example"></a>範例

```
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