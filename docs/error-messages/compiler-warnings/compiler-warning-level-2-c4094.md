---
title: 編譯器警告（層級2） C4094
ms.date: 11/04/2016
f1_keywords:
- C4094
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
ms.openlocfilehash: c293522e5d60d0edb4cc2da289e0ece71f89329f
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052207"
---
# <a name="compiler-warning-level-2-c4094"></a>編譯器警告（層級2） C4094

未標記的 ' token ' 未宣告符號

編譯器偵測到使用未標記結構、聯集或類別的空宣告。 宣告會被忽略。

## <a name="example"></a>範例

```cpp
// C4094.cpp
// compile with: /W2
struct
{
};   // C4094

int main()
{
}
```

此條件會在 ANSI 相容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下產生錯誤。