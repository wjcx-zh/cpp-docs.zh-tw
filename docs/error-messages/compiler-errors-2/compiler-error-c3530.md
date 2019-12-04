---
title: 編譯器錯誤 C3530
ms.date: 11/04/2016
f1_keywords:
- C3530
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
ms.openlocfilehash: 3766eaa83457ba6cffaf8b1599983a065772911c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750139"
---
# <a name="compiler-error-c3530"></a>編譯器錯誤 C3530

' auto ' 無法與任何其他類型規範結合

類型規範會與 `auto` 關鍵字搭配使用。

### <a name="to-correct-this-error"></a>若要改正這項錯誤

1. 請勿在使用 `auto` 關鍵字的變數宣告中使用類型規範。

## <a name="example"></a>範例

下列範例會產生 C3530，因為變數 `x` 是以 `auto` 關鍵字和類型 `int`來宣告，而且因為此範例是使用 **/zc： auto**所編譯。

```cpp
// C3530.cpp
// Compile with /Zc:auto
int main()
{
   auto int x;   // C3530
   return 0;
}
```

## <a name="see-also"></a>請參閱

[auto 關鍵字](../../cpp/auto-keyword.md)
