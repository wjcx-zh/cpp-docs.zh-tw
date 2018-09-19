---
title: 編譯器錯誤 C2687 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2687
dev_langs:
- C++
helpviewer_keywords:
- C2687
ms.assetid: 1d24b24a-cd0f-41cc-975c-b08dcfb7f402
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1333d26a7733ffeb0876a9b563377e5ead010261
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042672"
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