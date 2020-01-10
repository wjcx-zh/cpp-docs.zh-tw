---
title: 編譯器警告 (層級 4) C4918
ms.date: 11/04/2016
f1_keywords:
- C4918
helpviewer_keywords:
- C4918
ms.assetid: 1bcf6d35-3467-4aa8-b2ef-cb33f4e70238
ms.openlocfilehash: 801c22a45037492dc609d93c6339ab8feff30494
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988798"
---
# <a name="compiler-warning-level-4-c4918"></a>編譯器警告 (層級 4) C4918

'character' : 在 pragma 最佳化清單中的無效字元

在 [最佳化](../../preprocessor/optimize.md) pragma 陳述式的最佳化清單中找到未知的字元。

例如，下列陳述式會產生 C4918：

```cpp
// C4918.cpp
// compile with: /W4
#pragma optimize("X", on) // C4918 expected
int main()
{
}
```
