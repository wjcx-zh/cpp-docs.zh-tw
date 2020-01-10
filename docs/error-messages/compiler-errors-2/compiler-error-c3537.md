---
title: 編譯器錯誤 C3537
ms.date: 11/04/2016
f1_keywords:
- C3537
helpviewer_keywords:
- C3537
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
ms.openlocfilehash: ef3e954987b84ea128342b38307769903df4b346
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740477"
---
# <a name="compiler-error-c3537"></a>編譯器錯誤 C3537

' type '：您無法轉換成包含 ' auto ' 的類型

您無法將變數轉換成指定的類型，因為該類型包含 `auto` 關鍵字，且預設的[/zc： auto](../../build/reference/zc-auto-deduce-variable-type.md)編譯器選項已生效。

## <a name="example"></a>範例

下列程式碼會產生 C3537，因為變數會轉換成包含 `auto` 關鍵字的類型。

```cpp
// C3537.cpp
// Compile with /Zc:auto
int main()
{
   int value = 123;
   auto(value);                        // C3537
   (auto)value;                        // C3537
   auto x1 = auto(value);              // C3537
   auto x2 = (auto)value;              // C3537
   auto x3 = static_cast<auto>(value); // C3537
   return 0;
}
```

## <a name="see-also"></a>請參閱

[auto 關鍵字](../../cpp/auto-keyword.md)
