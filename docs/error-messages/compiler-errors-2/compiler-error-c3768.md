---
title: 編譯器錯誤 C3768
ms.date: 11/04/2016
f1_keywords:
- C3768
helpviewer_keywords:
- C3768
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
ms.openlocfilehash: e9c385fd178dc967e72f5e0ca7fab27b28ad962f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676725"
---
# <a name="compiler-error-c3768"></a>編譯器錯誤 C3768

> 無法取得純 managed 程式碼中的虛擬 vararg 函式的位址

## <a name="remarks"></a>備註

**/Clr: pure**編譯器選項是在 Visual Studio 2015 中已被取代，不支援的 Visual Studio 2017 中。

進行編譯時 **/clr: pure**，您無法取得的虛擬位址`vararg`函式。

## <a name="example"></a>範例

下列範例會產生 C3768:

```cpp
// C3768.cpp
// compile with: /clr:pure
struct A
{
   virtual void f(...);
};

int main()
{
   &(A::f);   // C3768
}
```