---
title: 編譯器警告（層級1） C4606
ms.date: 11/04/2016
f1_keywords:
- C4606
helpviewer_keywords:
- C4606
ms.assetid: c1b45fb6-672b-42eb-9e1c-c67b3e4150d3
ms.openlocfilehash: d36031aa9a831d4669d796d8a40292e2d6ba15a8
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73964970"
---
# <a name="compiler-warning-level-1-c4606"></a>編譯器警告（層級1） C4606

\#pragma 警告：已忽略 ' warning_number ';程式碼分析警告未與警告層級相關聯

針對程式碼分析警告，[警告](../../preprocessor/warning.md)pragma 僅支援 `error`、`once`和 `default`。

## <a name="example"></a>範例

下列範例會產生 C4606。

```cpp
// C4606.cpp
// compile with: /c /W1
#pragma warning(1: 6001)   // C4606
#pragma warning(once: 6001)   // OK
```