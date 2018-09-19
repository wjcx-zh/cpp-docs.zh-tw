---
title: 編譯器錯誤 C2081 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2081
dev_langs:
- C++
helpviewer_keywords:
- C2081
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 48f2cdecaea38beed14735bb3f94c8422a28c747
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030452"
---
# <a name="compiler-error-c2081"></a>編譯器錯誤 C2081

'identifier': 不合法的型式參數清單中的名稱

識別項會導致語法錯誤。

此錯誤可能被因使用舊樣式型式參數清單。 在型式參數清單中，您必須指定的型式參數的類型。

下列範例會產生 C2081:

```
// C2081.c
void func( int i, j ) {}  // C2081, no type specified for j
```

可能的解決方式：

```
// C2081b.c
// compile with: /c
void func( int i, int j ) {}
```