---
title: 編譯器錯誤 C2128
ms.date: 11/04/2016
f1_keywords:
- c2128
helpviewer_keywords:
- C2128
ms.assetid: 08cbf734-75b3-49f2-9026-9b319947612d
ms.openlocfilehash: 80015118bf9e8bc8d8c4fba578f4ff1fa4651034
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397636"
---
# <a name="compiler-error-c2128"></a>編譯器錯誤 C2128

'function': alloc_text/same_seg 僅適用使用 C 連結的函式

`pragma` `alloc_text` 僅能搭配具有 C 連結宣告的函式。

下列範例會產生 C2128:

```
// C2128.cpp
// compile with: /c

// Delete the following line to resolve.
void func();
// #pragma alloc_text("my segment", func)   // C2128

extern "C" {
void func();
}

#pragma alloc_text("my segment", func)
void func() {}
```