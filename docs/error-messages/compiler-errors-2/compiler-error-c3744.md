---
title: 編譯器錯誤 C3744
ms.date: 11/04/2016
f1_keywords:
- C3744
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
ms.openlocfilehash: 8db81afc348434e9ea2f57c991962fb15dc6bf98
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220154"
---
# <a name="compiler-error-c3744"></a>編譯器錯誤 C3744

__unhook 的 managed 事件必須至少有3個引數

在 [`__unhook`](../../cpp/unhook.md) 針對 Managed Extensions for C++ 編譯的程式中使用函式時，函式必須接受三個參數。

**`__hook`** 和 **`__unhook`** 與程式設計不相容 **`/clr`** 。 請改用 + = 和-= 運算子。

C3744 只能使用過時的編譯器選項來連接 **`/clr:oldSyntax`** 。
