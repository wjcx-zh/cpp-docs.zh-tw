---
title: 編譯器警告 （層級 1） C4079
ms.date: 11/04/2016
f1_keywords:
- C4079
helpviewer_keywords:
- C4079
ms.assetid: 549759f0-e168-47e9-8c9a-de93ac843689
ms.openlocfilehash: 8f9a9e05ab2a65ad954f9928f7b9fab0e7fee9cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564563"
---
# <a name="compiler-warning-level-1-c4079"></a>編譯器警告 （層級 1） C4079

未預期的語彙基元 'token'

Pragma 引數清單中，就會發生未預期的分隔符號語彙基元。 已忽略 pragma 的其餘部分。

下列範例會產生 C4079:

```
// C4079.cpp
// compile with: /W1
#pragma warning(disable : 4081)
#pragma pack(c,16)   // C4079

int main() {
}
```