---
title: 編譯器警告 （層級 1） C4659 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4659
dev_langs:
- C++
helpviewer_keywords:
- C4659
ms.assetid: e29ba8db-7917-43f6-8e34-868b752279ae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d00c54fa77d68722b2e47a9d49832911b398deca
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110052"
---
# <a name="compiler-warning-level-1-c4659"></a>編譯器警告 (層級 1) C4659

\#pragma 'pragma': 使用保留的區段 'segment' 有未定義的行為，請使用 #pragma 註解 (linker，...)

.Drectve 選項用來傳遞選項給連結器。 改為使用 pragma[註解](../../preprocessor/comment-c-cpp.md)傳遞連結器選項。

```
// C4659.cpp
// compile with: /W1 /LD
#pragma code_seg(".drectve")   // C4659
```