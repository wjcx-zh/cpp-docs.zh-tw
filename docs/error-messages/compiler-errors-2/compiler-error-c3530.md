---
title: 編譯器錯誤 C3530
ms.date: 11/04/2016
f1_keywords:
- C3530
helpviewer_keywords:
- C3530
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
ms.openlocfilehash: 152157824cb270f32b1233f39225abab7741eda5
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507063"
---
# <a name="compiler-error-c3530"></a>編譯器錯誤 C3530

' auto ' 無法與任何其他類型規範結合

類型規範會與關鍵字搭配使用 **`auto`** 。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 請勿在使用關鍵字的變數宣告中使用類型規範 **`auto`** 。

## <a name="example"></a>範例

下列範例會產生 C3530，因為變數 `x` 同時以 **`auto`** 關鍵字和類型宣告 **`int`** ，而且此範例是使用 **/zc： auto**來編譯。

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

[auto 關鍵字](../../cpp/auto-cpp.md)
