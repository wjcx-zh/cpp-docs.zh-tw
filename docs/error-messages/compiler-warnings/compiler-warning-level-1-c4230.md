---
title: 編譯器警告 (層級 1) C4230
ms.date: 11/04/2016
f1_keywords:
- C4230
helpviewer_keywords:
- C4230
ms.assetid: a4be8729-74b6-44df-a5ea-e3f45aad0f8f
ms.openlocfilehash: 0b590eaef2094c3d1c3a83541e9d5e10415928f9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223209"
---
# <a name="compiler-warning-level-1-c4230"></a>編譯器警告 (層級 1) C4230

使用過時：修飾詞/限定詞交錯;已忽略限定詞

在 Microsoft 修飾詞（例如）之前使用限定詞 **`__cdecl`** 是過時的作法。

## <a name="example"></a>範例

```cpp
// C4230.cpp
// compile with: /W1 /LD
int __cdecl const function1();   // C4230 const ignored
```
