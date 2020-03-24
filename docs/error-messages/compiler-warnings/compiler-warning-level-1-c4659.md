---
title: 編譯器警告 (層級 1) C4659
ms.date: 11/04/2016
f1_keywords:
- C4659
helpviewer_keywords:
- C4659
ms.assetid: e29ba8db-7917-43f6-8e34-868b752279ae
ms.openlocfilehash: 1766cb285fa33d384d57e89c7243fc35022ae006
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175632"
---
# <a name="compiler-warning-level-1-c4659"></a>編譯器警告 (層級 1) C4659

\#pragma ' pragma '：使用保留區段 ' 區段 ' 有未定義的行為，請使用 #pragma 批註（連結器，...）

Drectve 選項是用來將選項傳遞給連結器。 請改用 pragma [comment](../../preprocessor/comment-c-cpp.md)來傳遞連結器選項。

```cpp
// C4659.cpp
// compile with: /W1 /LD
#pragma code_seg(".drectve")   // C4659
```
