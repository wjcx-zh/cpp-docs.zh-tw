---
title: 編譯器警告 （層級 1） C4230 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4230
dev_langs:
- C++
helpviewer_keywords:
- C4230
ms.assetid: a4be8729-74b6-44df-a5ea-e3f45aad0f8f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb091b6cffe0bc049e7501fb006b1c84d9e0f6d2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112482"
---
# <a name="compiler-warning-level-1-c4230"></a>編譯器警告 (層級 1) C4230

過時的用法： 修飾詞/限定詞位置顛倒;已忽略限定詞

這類使用之前的 Microsoft 修飾詞的限定詞`__cdecl`是過時的作法。

## <a name="example"></a>範例

```
// C4230.cpp
// compile with: /W1 /LD
int __cdecl const function1();   // C4230 const ignored
```