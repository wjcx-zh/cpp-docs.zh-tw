---
title: 編譯器錯誤 C3537
ms.date: 11/04/2016
f1_keywords:
- C3537
helpviewer_keywords:
- C3537
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
ms.openlocfilehash: 22387470019b0118d06b4cacd82a1df5c3e505fb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50576120"
---
# <a name="compiler-error-c3537"></a>編譯器錯誤 C3537

'type': 您無法轉換成包含 'auto' 的類型

您無法轉換為指定的類型的變數，因為類型包含`auto`關鍵字和預設[/zc: auto](../../build/reference/zc-auto-deduce-variable-type.md)編譯器選項處於作用中。

## <a name="example"></a>範例

因為變數會轉換成此型別包含下列程式碼會產生 C3537`auto`關鍵字。

```
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

## <a name="see-also"></a>另請參閱

[auto 關鍵字](../../cpp/auto-keyword.md)