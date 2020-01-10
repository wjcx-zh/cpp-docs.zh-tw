---
title: 編譯器警告 (層級 4) C4429
ms.date: 11/04/2016
f1_keywords:
- C4429
helpviewer_keywords:
- C4429
ms.assetid: a3e4cf1f-a869-4e47-834a-850c21eb5297
ms.openlocfilehash: 6702db4af5c31d21610e02b1a4ec75af27ad10f2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990821"
---
# <a name="compiler-warning-level-4-c4429"></a>編譯器警告 (層級 4) C4429

可能是不完整或格式不正確的通用字元名稱

編譯器偵測到可能是格式不正確之通用字元名稱的字元序列。 通用字元名稱 `\u` 後面接著四個十六進位數位，或 `\U` 後面接著八個十六進位數位。

下列範例會產生 C4429：

```cpp
// C4429.cpp
// compile with: /W4 /WX
int \ug0e4 = 0;   // C4429
// Try the following line instead:
// int \u00e4 = 0;   // OK, a well-formed universal character name.
```
