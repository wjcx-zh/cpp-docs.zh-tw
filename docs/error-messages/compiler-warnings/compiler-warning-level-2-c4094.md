---
title: 編譯器警告（層級2） C4094
ms.date: 11/04/2016
f1_keywords:
- C4094
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
ms.openlocfilehash: c90ad202e193f21955d396dd2aff6b39d3a968c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174332"
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
