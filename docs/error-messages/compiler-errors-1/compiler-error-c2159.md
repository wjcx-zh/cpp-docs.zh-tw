---
title: 編譯器錯誤 C2159
ms.date: 11/04/2016
f1_keywords:
- C2159
helpviewer_keywords:
- C2159
ms.assetid: 925a2cbd-43c9-45ee-a373-84004350b380
ms.openlocfilehash: fd845fffe9778e51af7db77144607233ed9ddefd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174844"
---
# <a name="compiler-error-c2159"></a>編譯器錯誤 C2159

已經指定一個以上的儲存類別

一個宣告包含多個儲存類別。

下列範例會產生 C2159：

```
// C2159.cpp
// compile with: /c
static int i;   // OK
extern static int i;   // C2159
```