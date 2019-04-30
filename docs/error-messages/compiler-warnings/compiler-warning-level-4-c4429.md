---
title: 編譯器警告 (層級 4) C4429
ms.date: 11/04/2016
f1_keywords:
- C4429
helpviewer_keywords:
- C4429
ms.assetid: a3e4cf1f-a869-4e47-834a-850c21eb5297
ms.openlocfilehash: d4eb7e7075c7adf418254e748f104a6d57c72741
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391526"
---
# <a name="compiler-warning-level-4-c4429"></a>編譯器警告 (層級 4) C4429

可能不完整或格式不正確通用字元名稱

編譯器偵測到可能是格式不正確的通用字元名稱的字元序列。 通用字元名稱是`\u`後面接著四個十六進位數字，或`\U`後面接著八個十六進位數字。

下列範例會產生 C4429:

```
// C4429.cpp
// compile with: /W4 /WX
int \ug0e4 = 0;   // C4429
// Try the following line instead:
// int \u00e4 = 0;   // OK, a well-formed universal character name.
```