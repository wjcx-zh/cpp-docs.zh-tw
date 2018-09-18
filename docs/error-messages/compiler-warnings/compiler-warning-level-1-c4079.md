---
title: 編譯器警告 （層級 1） C4079 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4079
dev_langs:
- C++
helpviewer_keywords:
- C4079
ms.assetid: 549759f0-e168-47e9-8c9a-de93ac843689
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7de3eca54ddadd5c7a1687d4f7ebc5f6359a464e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073993"
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