---
title: 編譯器錯誤 C2464 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2464
dev_langs:
- C++
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff74085364d6638772ab2376aace93fea741056b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103136"
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