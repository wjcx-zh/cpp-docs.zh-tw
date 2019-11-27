---
title: 編譯器警告 (層級 4) C4201
ms.date: 11/04/2016
f1_keywords:
- C4201
helpviewer_keywords:
- C4201
ms.assetid: 6156f508-9393-4d77-9e73-1ec3e1c32d0d
ms.openlocfilehash: 1f029d7717f99e55a977ad9cb80dacbfa1485086
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541220"
---
# <a name="compiler-warning-level-4-c4201"></a>編譯器警告 (層級 4) C4201

使用非標準的擴充：不帶結構/聯集

在 [Microsoft 擴充功能（/Ze）] 底下，您可以指定不含宣告子的結構做為另一個結構或等位的成員。 這些結構會在 ANSI 相容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下產生錯誤。

## <a name="example"></a>範例

```cpp
// C4201.cpp
// compile with: /W4
struct S
{
   float y;
   struct
   {
      int a, b, c;  // C4201
   };
} *p_s;

int main()
{
}
```