---
title: 編譯器錯誤 C2054 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2054
dev_langs:
- C++
helpviewer_keywords:
- C2054
ms.assetid: 37f7c612-0d7d-4728-9e67-ac4160555f48
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5fc936bf6c42144a55bc6d84a8434959383e7e9f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071428"
---
# <a name="compiler-error-c2054"></a>編譯器錯誤 C2054

必須是 ' (' 遵循 'identifier'

需要後端的括號內容中使用函式識別項。

此錯誤可能被因省略複雜初始化等號 （=）。

下列範例會產生 C2054:

```
// C2054.c
int array1[] { 1, 2, 3 };   // C2054, missing =
```

可能的解決方式：

```
// C2054b.c
int main() {
   int array2[] = { 1, 2, 3 };
}
```