---
title: 編譯器錯誤 C2286
ms.date: 11/04/2016
f1_keywords:
- C2286
helpviewer_keywords:
- C2286
ms.assetid: 078e0201-35cc-42e2-8dbc-6f8cf557b098
ms.openlocfilehash: 7d3b8297c5f5da29b99abe78999396e8c44df0fd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182765"
---
# <a name="compiler-error-c2286"></a>編譯器錯誤 C2286

'identifier' 表示的成員指標已經設定為 '繼承'-忽略宣告

類別有兩種不同的指標至成員表示法。

如需詳細資訊，請參閱 <<c0> [ 繼承關鍵字](../../cpp/inheritance-keywords.md)。

## <a name="example"></a>範例

下列範例會產生 C2286：

```
// C2286.cpp
// compile with: /c
class __single_inheritance X;
class __multiple_inheritance X;   // C2286
class  __multiple_inheritance Y;   // OK
```