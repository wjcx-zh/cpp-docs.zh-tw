---
title: 編譯器錯誤 C2734 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2734
dev_langs:
- C++
helpviewer_keywords:
- C2734
ms.assetid: e53a77b7-825c-42d1-a655-90e1c93b833e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc3322d97761f1a463426c71bde58de3591ded4a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100704"
---
# <a name="compiler-error-c2734"></a>編譯器錯誤 C2734

'identifier': 必須初始化常數物件，如果不 extern

識別項宣告`const`但未初始化或`extern`。

下列範例會產生 C2734:

```
// C2734.cpp
const int j;   // C2734
extern const int i;   // OK, declared as extern
```