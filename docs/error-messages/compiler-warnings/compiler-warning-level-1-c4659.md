---
title: 編譯器警告（層級1） C4659
ms.date: 11/04/2016
f1_keywords:
- C4659
helpviewer_keywords:
- C4659
ms.assetid: e29ba8db-7917-43f6-8e34-868b752279ae
ms.openlocfilehash: 27023e6886638be63db1e1fb654c0caa70769a56
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052536"
---
# <a name="compiler-warning-level-1-c4659"></a>編譯器警告（層級1） C4659

\#pragma ' pragma '：使用保留區段 ' 區段 ' 有未定義的行為，請使用 #pragma 批註（連結器，...）

Drectve 選項是用來將選項傳遞給連結器。 請改用 pragma [comment](../../preprocessor/comment-c-cpp.md)來傳遞連結器選項。

```cpp
// C4659.cpp
// compile with: /W1 /LD
#pragma code_seg(".drectve")   // C4659
```