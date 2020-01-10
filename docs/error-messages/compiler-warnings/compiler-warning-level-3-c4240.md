---
title: 編譯器警告（層級3） C4240
ms.date: 11/04/2016
f1_keywords:
- C4240
helpviewer_keywords:
- C4240
ms.assetid: a2657cdb-18e1-493f-882b-4e10c0bca71d
ms.openlocfilehash: 3636e902e8d6ecd34cdc3e1135761c8595dc5998
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051749"
---
# <a name="compiler-warning-level-3-c4240"></a>編譯器警告（層級3） C4240

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