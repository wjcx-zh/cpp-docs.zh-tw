---
title: 編譯器警告 (層級 4) C4670
ms.date: 11/04/2016
f1_keywords:
- C4670
helpviewer_keywords:
- C4670
ms.assetid: e172b134-b1fb-4dfe-8e9d-209ea08b73c7
ms.openlocfilehash: 3ea32e8693fbe310b82eeeb87b1e97f2281ddf04
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990747"
---
# <a name="compiler-warning-level-4-c4670"></a>編譯器警告 (層級 4) C4670

'identifier': 此基底類別無法存取

無法存取要在 **try** 區塊中擲回之物件的指定基底類別。 如果擲回物件，則無法具現化物件。 請檢查使用正確的存取規範來繼承基底類別。

下列範例會產生 C4670：

```cpp
// C4670.cpp
// compile with: /EHsc /W4
class A
{
};

class B : /* public */ A
{
} b;   // inherits A with private access by default

int main()
{
    try
    {
       throw b;   // C4670
    }
    catch( B )
    {
    }
}
```
