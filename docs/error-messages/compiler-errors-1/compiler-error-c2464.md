---
title: 編譯器錯誤 C2464
ms.date: 11/04/2016
f1_keywords:
- C2464
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
ms.openlocfilehash: e4952f4702d871ecf1c818b1fc7394e54a1a295f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743883"
---
# <a name="compiler-error-c2464"></a>編譯器錯誤 C2464

' identifier '：無法使用 ' new ' 來配置參考

已使用 `new` 運算子配置參考識別碼。 參考不是記憶體物件，因此 `new` 無法傳回指標。 使用標準變數宣告語法來宣告參考。

下列範例會產生 C2464：

```cpp
// C2464.cpp
int main() {
   new ( int& ir );   // C2464
}
```
