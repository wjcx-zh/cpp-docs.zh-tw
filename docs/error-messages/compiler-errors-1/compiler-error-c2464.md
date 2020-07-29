---
title: 編譯器錯誤 C2464
ms.date: 11/04/2016
f1_keywords:
- C2464
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
ms.openlocfilehash: b2d2766b11d15bdb666baa207591cc9ff279a280
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225471"
---
# <a name="compiler-error-c2464"></a>編譯器錯誤 C2464

' identifier '：無法使用 ' new ' 來配置參考

參考識別碼是使用運算子配置的 **`new`** 。 參考不是記憶體物件，因此 **`new`** 無法傳回它們的指標。 使用標準變數宣告語法來宣告參考。

下列範例會產生 C2464：

```cpp
// C2464.cpp
int main() {
   new ( int& ir );   // C2464
}
```
