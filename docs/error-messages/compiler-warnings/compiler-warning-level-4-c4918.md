---
title: 編譯器警告 （層級 4） C4918 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4918
dev_langs:
- C++
helpviewer_keywords:
- C4918
ms.assetid: 1bcf6d35-3467-4aa8-b2ef-cb33f4e70238
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb4cc66359c28ffc23afa64da1e5bdbaadd8fb9b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023224"
---
# <a name="compiler-warning-level-4-c4918"></a>編譯器警告 (層級 4) C4918

'character' : 在 pragma 最佳化清單中的無效字元

在 [最佳化](../../preprocessor/optimize.md) pragma 陳述式的最佳化清單中找到未知的字元。

例如，下列陳述式會產生 C4918：

```
// C4918.cpp
// compile with: /W4
#pragma optimize("X", on) // C4918 expected
int main()
{
}
```