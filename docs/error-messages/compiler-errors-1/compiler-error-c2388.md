---
title: 編譯器錯誤 C2388
ms.date: 11/04/2016
f1_keywords:
- C2388
helpviewer_keywords:
- C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
ms.openlocfilehash: 50148f4fb5c3af33d8de8b005f75f491b0540271
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225497"
---
# <a name="compiler-error-c2388"></a>編譯器錯誤 C2388

' symbol '：符號不能同時以 __declspec （appdomain）和 \_ _declspec （進程）宣告

和修飾詞 `appdomain` `process` **`__declspec`** 不能用在相同的符號上。 變數的儲存體依處理序或應用程式定義域而存在。

如需詳細資訊，請參閱 [appdomain](../../cpp/appdomain.md) 和 [處理序](../../cpp/process.md)。

下列範例會產生 C2388：

```cpp
// C2388.cpp
// compile with: /clr /c
__declspec(process) __declspec(appdomain) int i;   // C2388
__declspec(appdomain) int i;   // OK
```
