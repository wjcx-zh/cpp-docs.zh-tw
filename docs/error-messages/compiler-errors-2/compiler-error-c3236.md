---
title: 編譯器錯誤 C3236 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3236
dev_langs:
- C++
helpviewer_keywords:
- C3236
ms.assetid: 4ef1871f-a348-44ae-922b-1e2081de20d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ad012c067a5698eefa3f8a91e85252aef93d3e5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044388"
---
# <a name="compiler-error-c3236"></a>編譯器錯誤 C3236

不能對泛型類別進行明確執行個體化

編譯器不允許明確具現化泛型類別。

下列範例會產生 C3236：

```
// C3236.cpp
// compile with: /clr
generic<class T>
public ref class X {};

generic ref class X<int>;   // C3236
```

下列範例示範可能的解決方式：

```
// C3236b.cpp
// compile with: /clr /c
generic<class T>
public ref class X {};
```