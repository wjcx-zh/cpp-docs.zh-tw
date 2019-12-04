---
title: 編譯器錯誤 C2147
ms.date: 11/04/2016
f1_keywords:
- C2147
helpviewer_keywords:
- C2147
ms.assetid: d1adb3bf-7ece-4815-922c-ad7492fb6670
ms.openlocfilehash: 0af88d89ff264ca9efd02477a62e5bd7532271bd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756483"
---
# <a name="compiler-error-c2147"></a>編譯器錯誤 C2147

語法錯誤： ' identifier ' 是新的關鍵字

使用的識別碼現在是語言中的保留關鍵字。

下列範例會產生 C2147：

```cpp
// C2147.cpp
// compile with: /clr
int main() {
   int gcnew = 0;   // C2147
   int i = 0;   // OK
}
```
