---
title: 編譯器錯誤 C3156
ms.date: 11/04/2016
f1_keywords:
- C3156
helpviewer_keywords:
- C3156
ms.assetid: 1876da78-b94e-4af7-9795-28f72b209b3e
ms.openlocfilehash: 115e8cd63562964b19e4a67f7a649ecfab2596c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465256"
---
# <a name="compiler-error-c3156"></a>編譯器錯誤 C3156

'class'：您無法具有一個 managed 或 WinRT 類型的本機定義

函式不可包含 managed 或 WinRT 類別、結構或介面的定義或宣告。

## <a name="example"></a>範例

下列範例會產生 C3156。

```
// C3156.cpp
// compile with: /clr /c
void f() {
   ref class X {};   // C3156
   ref class Y;   // C3156
}
```
