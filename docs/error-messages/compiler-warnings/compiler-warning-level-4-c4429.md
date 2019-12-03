---
title: 編譯器警告 (層級 4) C4429
ms.date: 11/04/2016
f1_keywords:
- C4429
helpviewer_keywords:
- C4429
ms.assetid: a3e4cf1f-a869-4e47-834a-850c21eb5297
ms.openlocfilehash: e814867278701be11b0158789f6373453aea75b8
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683242"
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