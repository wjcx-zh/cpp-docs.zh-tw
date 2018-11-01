---
title: 編譯器錯誤 C2687
ms.date: 11/04/2016
f1_keywords:
- C2687
helpviewer_keywords:
- C2687
ms.assetid: 1d24b24a-cd0f-41cc-975c-b08dcfb7f402
ms.openlocfilehash: a30efa264a4e7be387c3c2363940bd5ceca1bcc4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540942"
---
# <a name="compiler-error-c2687"></a>編譯器錯誤 C2687

'type': 例外狀況宣告不能是 'void' 或代表不完整的類型或指標或參考不完整的類型

針對要納入例外狀況宣告的類型，它必須是已定義且非 void。

下列範例會產生 C2687:

```
// C2687.cpp
class C;

int main() {
   try {}
   catch (C) {}   // C2687 error
}
```

可能的解決方式：

```
// C2687b.cpp
// compile with: /EHsc
class C {};

int main() {
   try {}
   catch (C) {}
}
```