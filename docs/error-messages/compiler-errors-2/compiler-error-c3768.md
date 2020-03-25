---
title: 編譯器錯誤 C3768
ms.date: 11/04/2016
f1_keywords:
- C3768
helpviewer_keywords:
- C3768
ms.assetid: 091f0d53-1dff-43fd-813d-5c43c85b6ab0
ms.openlocfilehash: 534be9e3873276313335ca921264be92c9259b93
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165739"
---
# <a name="compiler-error-c3768"></a>編譯器錯誤 C3768

> 無法在純粹的 managed 程式碼中採用虛擬 vararg 函式的位址

## <a name="remarks"></a>備註

**/Clr： pure**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

以 **/clr： pure**進行編譯時，您無法接受虛擬 `vararg` 函式的位址。

## <a name="example"></a>範例

下列範例會產生 C3768：

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
