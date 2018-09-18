---
title: 編譯器錯誤 C2238 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2238
dev_langs:
- C++
helpviewer_keywords:
- C2238
ms.assetid: 3d53060c-d6b7-4603-b9cf-d7c65eb64cd2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a1af9ef4f36198190d174d69ec825aa6e655616
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065981"
---
# <a name="compiler-error-c2238"></a>編譯器錯誤 C2238

在 'token' 之前有未預期的語彙基元

找到不正確的語彙基元。

下列範例會產生 C2238：

```
// C2238.cpp
// compile with: /c
class v {
virtual: int vvv;   // C2238
};
```