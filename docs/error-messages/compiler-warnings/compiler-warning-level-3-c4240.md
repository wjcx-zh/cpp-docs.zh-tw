---
title: 編譯器警告 (層級 3) C4240
ms.date: 11/04/2016
f1_keywords:
- C4240
helpviewer_keywords:
- C4240
ms.assetid: a2657cdb-18e1-493f-882b-4e10c0bca71d
ms.openlocfilehash: 9e4d33bd0151e4355903c7d10b667ced405a2471
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161564"
---
# <a name="compiler-warning-level-3-c4240"></a>編譯器警告 (層級 3) C4240

使用非標準的擴充： ' classname ' 的存取現在已定義為「存取規範」，先前已定義為「存取規範」

在 ANSI 相容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下，您無法變更嵌套類別的存取權。 在預設的 Microsoft extensions （/Ze）底下，您可以使用此警告來進行。

## <a name="example"></a>範例

```cpp
// C4240.cpp
// compile with: /W3
class X
{
private:
   class N;
public:
   class N
   {   // C4240
   };
};

int main()
{
}
```
