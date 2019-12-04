---
title: 編譯器錯誤 C2286
ms.date: 11/04/2016
f1_keywords:
- C2286
helpviewer_keywords:
- C2286
ms.assetid: 078e0201-35cc-42e2-8dbc-6f8cf557b098
ms.openlocfilehash: 79697a17d322ae15a21e522efa7dfd5c2342f7a6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759161"
---
# <a name="compiler-error-c2286"></a>編譯器錯誤 C2286

' identifier ' 表示的成員指標已設定為 ' 繼承 '-已忽略宣告

類別有兩個不同的成員指標標記法。

如需詳細資訊，請參閱[繼承關鍵字](../../cpp/inheritance-keywords.md)。

## <a name="example"></a>範例

下列範例會產生 C2286：

```cpp
// C2286.cpp
// compile with: /c
class __single_inheritance X;
class __multiple_inheritance X;   // C2286
class  __multiple_inheritance Y;   // OK
```
