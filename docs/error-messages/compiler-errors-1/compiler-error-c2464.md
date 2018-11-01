---
title: 編譯器錯誤 C2464
ms.date: 11/04/2016
f1_keywords:
- C2464
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
ms.openlocfilehash: a00ac997f73175eeab08a0132128e48e8fc58feb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498185"
---
# <a name="compiler-error-c2464"></a>編譯器錯誤 C2464

'identifier': 無法使用 'new' 來配置參考

參考識別碼已配置具有`new`運算子。 參考不是記憶體物件，因此`new`無法傳回指標給他們。 您可以使用標準的變數宣告語法來宣告參考。

下列範例會產生 C2464:

```
// C2464.cpp
int main() {
   new ( int& ir );   // C2464
}
```