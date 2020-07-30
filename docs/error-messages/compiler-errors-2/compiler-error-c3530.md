---
title: 編譯器錯誤 C3530
ms.date: 11/04/2016
f1_keywords:
- C3530
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
ms.openlocfilehash: 023d7f0a5d509c4b301a9985da8ea7feb1f3d203
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228826"
---
# <a name="compiler-error-c3530"></a>編譯器錯誤 C3530

' auto ' 無法與任何其他類型規範結合

類型規範與關鍵字搭配使用 **`auto`** 。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 請勿在使用關鍵字的變數宣告中使用類型規範 **`auto`** 。

## <a name="example"></a>範例

下列範例會產生 C3530，因為變數 `x` 是以 **`auto`** 關鍵字和類型宣告 **`int`** ，而且範例是使用 **/zc： auto**所編譯。

```cpp
// C3530.cpp
// Compile with /Zc:auto
int main()
{
   auto int x;   // C3530
   return 0;
}
```

## <a name="see-also"></a>另請參閱

[auto 關鍵字](../../cpp/auto-keyword.md)
