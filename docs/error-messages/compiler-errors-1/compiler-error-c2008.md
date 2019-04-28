---
title: 編譯器錯誤 C2008
ms.date: 11/04/2016
f1_keywords:
- C2008
helpviewer_keywords:
- C2008
ms.assetid: e748ccbe-ffd4-4008-aca7-e53c25225209
ms.openlocfilehash: 0bd9193d6e305a4b6c6851ef2524a68ecc056816
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208980"
---
# <a name="compiler-error-c2008"></a>編譯器錯誤 C2008

'character'：未預期會出現在巨集定義中

字元，會緊接巨集名稱。 若要解決此錯誤，必須有空格之後巨集名稱。

下列範例會產生 C2008:

```
// C2008.cpp
#define TEST1"mytest1"    // C2008
```

可能的解決方式：

```
// C2008b.cpp
// compile with: /c
#define TEST2 "mytest2"
```