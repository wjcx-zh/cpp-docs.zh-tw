---
title: 編譯器錯誤 C2055
ms.date: 11/04/2016
f1_keywords:
- C2055
helpviewer_keywords:
- C2055
ms.assetid: 6cec79cc-6bec-443f-9897-fbf5452718c7
ms.openlocfilehash: 9cb6e4d5891c5aefc9d66e7d70a5cd7685ccd393
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302038"
---
# <a name="compiler-error-c2055"></a>編譯器錯誤 C2055

預期的型式參數清單，而不是類型清單

函式定義包含參數類型清單，而不是型式參數清單。 ANSI C 必須命名正式參數，除非它們是 void 或省略號（`...`）。

下列範例會產生 C2055：

```c
// C2055.c
// compile with: /c
void func(int, char) {}  // C2055
void func (int i, char c) {}   // OK
```
